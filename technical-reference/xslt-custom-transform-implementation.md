---
title: XSLT custom transform implementation (Grid Property)
TOCTitle: XSLT custom transform implementation (Grid Property)
ms:assetid: 9e206d6d-55f4-41bf-a46a-29e33fe324fd
ms:mtpsurl: https://msdn.microsoft.com/library/Aa577606(v=BTS.80)
ms:contentKeyID: 51530003
ms.date: 08/30/2017
mtps_version: v=BTS.80
---

# XSLT custom transform implementation (Grid Property)

## ITransform2 class.
 XSLT custom transform should implement abstract class ITransform2.

```C#
    public abstract class ITransform2
    {
       // This is not required, user can implement if they want their transform support custom extension.
       // These 3 parameters passed in are from "Custom Extension XML", in which user can provide namespace, assembly name, class name of the extension object, here user should create the extension behavior, like extension object creation, and registry.
        public virtual void RegisterExtension(string namespaceUri, string assemblyName, string className)
               
        // Load XSLT string.
        public abstract void Load(string xslt);

        // Transform input stream into out string.
        // Notice BizTalk actually doesn't support xslt arguments for now, it is reserved for future usage.
        public abstract void Transform(Stream input, IDictionary<XmlQualifiedName, object> xsltArguments, Stream results);
    }
```

## Example implementation

```C#
using System;
using System.Collections.Generic;
using System.Globalization;
using System.IO;
using System.Reflection;
using System.Xml;
using Microsoft.BizTalk.ScalableTransformation;
using Microsoft.XLANGs.BaseTypes;
using Saxon.Api;

namespace CustomTransform
{
    public class SaxonEEXsltTransform : ITransform2
    {
        protected bool legacyWhitespaceBehavior;
        protected Processor processor;
        protected XsltCompiler compiler;
        protected Xslt30Transformer transformer;

        public SaxonEEXsltTransform()
        {
            this.legacyWhitespaceBehavior = Microsoft.BizTalk.ScalableTransformation.BTSXslTransform.LegacyWhitespaceBehavior;

			// You have to put your license file in the designated place if you set "licensedEdition" as true. 
            this.processor = new Processor(true);

            this.processor.SetProperty(FeatureKeys.STRIP_WHITESPACE, this.legacyWhitespaceBehavior ? "all" : "none");
            this.compiler = processor.NewXsltCompiler();
        }

        public override void RegisterExtension(string namespaceUri, string assemblyName, string className)
        {
            Assembly assembly = Assembly.Load(assemblyName);
            Object obj = assembly.CreateInstance(className);

            ExtensionFunction function = obj as ExtensionFunction;
            if (function != null)
            {
                this.processor.RegisterExtensionFunction(function);
            }

            ExtensionFunctionDefinition functionDefinition = obj as ExtensionFunctionDefinition;
            if (functionDefinition != null)
            {
                this.processor.RegisterExtensionFunction(functionDefinition);
            }

            if (function == null && functionDefinition == null)
            {
                throw new ArgumentException(string.Format("Invalid extension class {0}, it should be of type {1} or {2}.", className, typeof(ExtensionFunction).Name, typeof(ExtensionFunctionDefinition).Name));
            }
        }

        public override void Load(string xslt)
        {
            XsltExecutable executable = this.compiler.Compile(new StringReader(xslt));
            this.transformer = executable.Load30();
        }

        public override void Transform(Stream input, IDictionary<XmlQualifiedName, object> xsltArguments, Stream results)
        {
            if (xsltArguments != null)
            {
                Dictionary<QName, XdmValue> parameters = new Dictionary<QName, XdmValue>();
                foreach (XmlQualifiedName name in xsltArguments.Keys)
                {
                    parameters[new QName(name)] = new XdmExternalObjectValue(xsltArguments[name]);
                }

                this.transformer.SetStylesheetParameters(parameters);
            }

            this.transformer.InputXmlResolver = new XmlUrlResolver();
            Serializer serializer = processor.NewSerializer();
            serializer.SetOutputStream(results);
            this.transformer.ApplyTemplates(input, serializer);
            serializer.Close();
        }
    }
}
```



## See Also

[XSLT custom transform engine property](xslt-transform-engine-grid-properties.md)

