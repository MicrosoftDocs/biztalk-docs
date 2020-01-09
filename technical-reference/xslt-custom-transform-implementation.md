---
# required metadata

title: Custom XSLT transform implementation
description: Custom XSLT transform implementation
author: Elvis-Shi
ms.author: elsh
manager: dougeby
ms.date: 01/06/2029
ms.topic: conceptual
ms.prod: biztalk-server
# optional metadata

#ROBOTS:

ms.reviewer: 
ms.suite:
ms.tgt_pltfrm:
ms.assetid: 
ms.custom: biztalk-2020
---

# Custom XSLT transform implementation

## ITransform2 class.
 **Start from BizTalk Server 2020**, custom XSLT transform engine is supported for BizTalk map. You can implement custom XSLT transform engine by defining XSLT transform implementation derived from abstract class Microsoft.XLANGs.BaseTypes.ITransform2 in assembly Microsoft.XLANGs.BaseTypes.dll.

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

[XSLT custom transform engine property](xslt-transform-engine-grid-property.md)

[Custom Extension XML](custom-extension-xml-grid-property.md)
