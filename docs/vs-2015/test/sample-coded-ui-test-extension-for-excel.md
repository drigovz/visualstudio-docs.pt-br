---
title: Extensão de teste de IU codificado de exemplo para Excel | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-test
ms.topic: conceptual
helpviewer_keywords:
- coded UI tests, extensions for Excel
ms.assetid: 451e4d14-7fac-42f9-af56-2bdc8414c6c7
caps.latest.revision: 15
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: e0c6075f9f95f7dc1d21db91936cf35c76f9b2e5
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72672237"
---
# <a name="sample-coded-ui-test-extension-for-excel"></a>Extensão de teste de IU codificado de amostra para Excel
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

O componente de extensão da amostra é executado no processo de teste de IU codificado do [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] e é ligeiramente hierárquico com a classe `ExtensionPackage` na base. As classes `TechnologyManager`, `ActionFilter` e `PropertyProvider` estão no próximo nível, com os elementos de controle no nível superior.

 ![Arquitetura de extensão de teste do Excel](../test/media/excel-extarch.png "Excel_ExtArch") Arquitetura de extensão do Excel

## <a name="extension-points"></a>Pontos de extensão
 Essas classes representam os pontos de extensão implementados na amostra para habilitar o teste para de IU codificado para [!INCLUDE[ofprexcel](../includes/ofprexcel-md.md)].

### <a name="extensionpackage"></a>ExtensionPackage
 Herdado da classe <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITestExtensionPackage>, este é o ponto de entrada para o extensão de teste de IU codificado. A implementação dessa classe abstrata fornece o acesso interno ao framework de teste de IU codificado para seu gerente de tecnologia de teste de IU personalizado, provedor de propriedade de teste de IU e o filtro de ação de teste de IU para testar a nova IU. Para obter mais informações, consulte [Classe ExtensionPackage](../test/sample-excel-extension-extensionpackage-class.md).

### <a name="technologymanager"></a>TechnologyManager
 Herdada da classe <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyManager>, essa classe fornece um gerente de tecnologia para gravação e reprodução de teste. Para obter mais informações, consulte [Classe TechnologyManager](../test/sample-excel-extension-technologymanager-class.md).

### <a name="actionfilter"></a>ActionFilter
 Herdado da classe [UITestActionFilter](/previous-versions/visualstudio/visual-studio-2012/dd985757(v=vs.110)) , essa classe fornece uma classe base para agregar resultados de ação de teste semelhantes em um único resultado de teste. Para obter mais informações, consulte [Classe ActionFilter](../test/sample-excel-extension-actionfilter-class.md).

### <a name="technology-elements"></a>Elementos de tecnologia
 Uma classe base herdada da classe <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyElement> fornece a base para os elementos de tecnologia em seus testes de interface do usuário que podem ser registrados e reproduzidos. Para obter mais informações, consulte [Classes de Elemento](../test/sample-excel-extension-element-classes.md).

### <a name="propertyprovider"></a>PropertyProvider
 Herdada da classe <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestPropertyProvider>, essa classe fornece uma classe base para dar suporte às propriedades dos elementos de interface do usuário para gravação e reprodução de teste. Para obter mais informações, consulte [Classe PropertyProvider](../test/sample-excel-extension-propertyprovider-class.md).

## <a name="see-also"></a>Confira também

- <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestPropertyProvider>
- <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyElement>
- <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITestExtensionPackage>
- [ExtensionPackage Class](../test/sample-excel-extension-extensionpackage-class.md)
- [Classe TechnologyManager](../test/sample-excel-extension-technologymanager-class.md)
- [Classe ActionFilter](../test/sample-excel-extension-actionfilter-class.md)
- [Classes Element](../test/sample-excel-extension-element-classes.md)
- [Classe PropertyProvider](../test/sample-excel-extension-propertyprovider-class.md)
