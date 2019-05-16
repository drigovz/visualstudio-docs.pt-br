---
title: 'CA3076: Execução de Script XSLT não | Microsoft Docs'
ms.date: 11/15/2016
ms.technology: vs-ide-code-analysis
ms.topic: reference
ms.assetid: 53cb7a46-c564-488f-bc51-0e210a7853c9
caps.latest.revision: 7
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 0a6b1efa5b5ee84092531a67421d03583afc3578
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65680727"
---
# <a name="ca3076-insecure-xslt-script-execution"></a>CA3076: Execução de script XSLT não seguro
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|NomeDoTipo|InsecureXSLTScriptExecution|
|CheckId|CA3076|
|Categoria|Microsoft.Security|
|Alteração Significativa|Não separável|

## <a name="cause"></a>Causa
 Se você executar [extensível folhas de estilos XSLT (linguagem)](https://support.microsoft.com/kb/313997) em aplicativos .NET de maneira insegura, o processador pode [resolver referências de URI não confiáveis](https://msdn.microsoft.com/ba3e4d4f-1ee7-4226-a51a-78a1f1b5bd8a) que poderia revelar confidenciais informações para invasores, levando a ataques de negação de serviço e Cross-Site.

## <a name="rule-description"></a>Descrição da Regra
 [XSLT](https://msdn.microsoft.com/6377ce5f-3c45-42a6-b7a9-ec8da588b60c) é um padrão de World Wide Web Consortium (W3C) para transformar os dados XML. XSLT normalmente é usado para gravar as folhas de estilo para transformar dados XML em outros formatos, como HTML, fixa comprimento texto, texto separado por vírgula ou outro formato XML. Embora proibidas por padrão, você pode optar por habilitá-la para seu projeto.

 Para garantir que você não estiver expondo uma superfície de ataque, essa regra dispara sempre que o XslCompiledTransform.<xref:System.Xml.Xsl.XslCompiledTransform.Load%2A> recebe a instâncias de combinação inseguro de <xref:System.Xml.Xsl.XsltSettings> e <xref:System.Xml.XmlResolver>, que permite o processamento de script mal-intencionado.

## <a name="how-to-fix-violations"></a>Como Corrigir Violações

- Substitua o argumento XsltSettings inseguro XsltSettings.<xref:System.Xml.Xsl.XsltSettings.Default%2A> ou, com uma instância que desabilitou a execução de script e a função do documento.

- Substitua os <xref:System.Xml.XmlResolver> argumento com null ou um <xref:System.Xml.XmlSecureResolver> instância.

## <a name="when-to-suppress-warnings"></a>Quando Suprimir Avisos
 A menos que você tiver certeza de que a entrada é conhecida por ser de uma fonte confiável, não suprima uma regra deste aviso.

## <a name="pseudo-code-examples"></a>Exemplos de código pseudo

### <a name="violation"></a>Violação

```csharp
using System.Xml;
using System.Xml.Xsl;

namespace TestNamespace
{
    class TestClass
    {
         void TestMethod()
        {
             XslCompiledTransform xslCompiledTransform = new XslCompiledTransform();
             var settings = XsltSettings.TrustedXslt;
             var resolver = new XmlUrlResolver();
             xslCompiledTransform.Load("testStylesheet", settings, resolver); // warn
        }
    }
} 
```

### <a name="solution"></a>Solução

```csharp
using System.Xml;
using System.Xml.Xsl;

namespace TestNamespace
{
    class TestClass
    {
        void TestMethod()
        {
            XslCompiledTransform xslCompiledTransform = new XslCompiledTransform();
            var settings = XsltSettings.Default;
            var resolver = new XmlUrlResolver();
            xslCompiledTransform.Load("testStylesheet", settings, resolver);
        }
    }
}
```

### <a name="violation"></a>Violação

```csharp
using System.Xml;
using System.Xml.Xsl;

namespace TestNamespace
{
    class TestClass
    {
        private static void TestMethod(XsltSettings settings)
        {
            try
            {
                XslCompiledTransform xslCompiledTransform = new XslCompiledTransform();
                var resolver = new XmlUrlResolver();
                xslCompiledTransform.Load("testStylesheet", settings, resolver); // warn
            }
            catch { throw; }
            finally { }
        }
    }
}
```

### <a name="solution"></a>Solução

```csharp
using System.Xml;
using System.Xml.Xsl;

namespace TestNamespace
{
    class TestClass
    {
        private static void TestMethod(XsltSettings settings)
        {
            try
            {
                XslCompiledTransform xslCompiledTransform = new XslCompiledTransform();
                settings.EnableDocumentFunction = false;
                settings.EnableScript = false;
                var resolver = new XmlUrlResolver();
                xslCompiledTransform.Load("testStylesheet", settings, resolver);
            }
            catch { throw; }
            finally { }
        }
    }
}
```
