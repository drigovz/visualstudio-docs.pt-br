---
title: 'Extensão de amostra do Excel: Classe ExtensionPackage | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-test
ms.topic: conceptual
ms.assetid: 6e45410a-1819-4d54-ac21-7280152f7e3a
caps.latest.revision: 11
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: a1c1f4c746fa505b50bab9caa7a516a2abc77f69
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72672205"
---
# <a name="sample-excel-extension-extensionpackage-class"></a>Extensão de exemplo do Excel: classe ExtensionPackage
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Essa classe estende a classe <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITestExtensionPackage> e fornece o ponto de entrada para a extensão de teste de IU codificado que está testando uma Planilha do [!INCLUDE[ofprexcel](../includes/ofprexcel-md.md)].

## <a name="assembly-attribute"></a>Atributos do Assembly
 O arquivo começa com um atributo de assembly que identifica o assembly como uma extensão de teste de interface do usuário.

```
[assembly: Microsoft.VisualStudio.TestTools.UITest.Extension.UITestExtensionPackage(
    "ExcelExtensionPackage",
    typeof(
     Microsoft.VisualStudio.Test.Sample.UI.ExtensionPackage))]
```

 Esse atributo declara o nome de classe base, o nome da classe de pacote e o nome de classe totalmente qualificado da classe de pacote de extensão personalizada.

## <a name="simple-properties"></a>Propriedades Simples
 Essa classe tem propriedades que fornecem valores que são usados pela estrutura de teste da interface do usuário codificada para identificar e descrever a extensão e o assembly. Consulte os comentários do código para obter mais informações.

## <a name="getservice-method"></a>Método GetService
 O método <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITestExtensionPackage.GetService%2A> é o único ponto de entrada usado pela estrutura de teste de IU codificado para obter acesso ao gerente de tecnologia, ao provedor de propriedade e ao filtro de ação, conforme identificado pela classe base de cada objeto.

## <a name="see-also"></a>Consulte Também
 <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITestExtensionPackage> [Estendendo testes de IU codificado e gravações da ação para dar suporte ao Microsoft Excel](../test/extending-coded-ui-tests-and-action-recordings-to-support-microsoft-excel.md)
