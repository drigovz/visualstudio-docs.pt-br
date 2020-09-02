---
title: Suporte para categorias de configurações | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: devlang-csharp
ms.topic: conceptual
helpviewer_keywords:
- settings, supporting with Visual Studio SDK
- Visual Studio SDK, supporting settings
ms.assetid: 3bac375d-8bd5-41be-a8de-32eb33c5cfac
caps.latest.revision: 20
manager: jillfra
ms.openlocfilehash: 15a3896f8a2010a063393d3a11c1ed3453a008d5
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65689095"
---
# <a name="support-for-settings-categories"></a>Suporte para categorias de configurações
Uma categoria de configurações consiste em um grupo de opções que personalizam o ambiente de desenvolvimento integrado (IDE). Por exemplo, as configurações podem controlar o layout do [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Windows e o conteúdo dos menus. Para obter mais informações, consulte [Personalizando configurações de desenvolvimento no Visual Studio](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
 No menu **ferramentas** , clique em **importar e exportar configurações** para iniciar o **Assistente de importação e exportação de configurações**. O assistente oferece três opções: exportar, importar ou redefinir suas configurações. A seleção de exportar, por exemplo, abre a página **escolher as configurações a serem exportadas** do assistente.  
  
 O controle de árvore no painel de navegação desta página lista categorias. Uma categoria é um grupo de configurações relacionadas que aparecem como um "ponto de configurações personalizadas", ou seja, como uma caixa de seleção. Use essas caixas de seleção para selecionar as categorias para persistir em um arquivo. vsettings. O assistente permite que você nomeie o arquivo. vsettings e especifique seu caminho.  
  
> [!NOTE]
> As configurações são salvas ou restauradas como uma categoria, e os nomes de configuração individuais não são exibidos no assistente.  
  
 A estrutura de pacote gerenciada (MPF) dá suporte à criação de categorias de configurações com um mínimo de código adicional.  
  
- Você cria um VSPackage para fornecer um contêiner para a categoria por meio da subclasse da <xref:Microsoft.VisualStudio.Shell.Package> classe.  
  
- Você cria a categoria em si, derivando-a da <xref:Microsoft.VisualStudio.Shell.DialogPage> classe.  
  
- Conecte os dois com o <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> .  
  
## <a name="support-for-settings-categories"></a>Suporte para categorias de configurações  
 A <xref:Microsoft.VisualStudio.Shell.Package> classe fornece suporte para a criação de categorias. A <xref:Microsoft.VisualStudio.Shell.DialogPage> classe implementa uma categoria. A implementação padrão do <xref:Microsoft.VisualStudio.Shell.DialogPage> oferece suas propriedades públicas para um usuário como uma categoria. Para obter mais informações, consulte [criando uma categoria de configurações](../extensibility/creating-a-settings-category.md).  
  
 A <xref:Microsoft.VisualStudio.Shell.DialogPage> classe implementa <xref:Microsoft.VisualStudio.Shell.IProfileManager> , que fornece persistência para ambas as páginas de opções e configurações de usuário. Os <xref:Microsoft.VisualStudio.Shell.IProfileManager.LoadSettingsFromXml%2A> <xref:Microsoft.VisualStudio.Shell.IProfileManager.SaveSettingsToXml%2A> métodos e persistem configurações em um arquivo. vssettings que [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] fornece como um <xref:Microsoft.VisualStudio.Shell.Interop.IVsSettingsReader> ou <xref:Microsoft.VisualStudio.Shell.Interop.IVsSettingsWriter> , respectivamente. O <xref:Microsoft.VisualStudio.Shell.IProfileManager.ResetSettings%2A> método redefine as configurações para seus valores padrão.  
  
 A <xref:Microsoft.VisualStudio.Shell.DialogPage> classe fornece uma implementação do <xref:Microsoft.VisualStudio.Shell.DialogPage.LoadSettingsFromXml%2A> método que lê pares de nome-valor do feed XML e usa reflexão para descobrir propriedades públicas na <xref:Microsoft.VisualStudio.Shell.DialogPage> classe derivada. As propriedades que têm nomes que correspondem aos pares de nome-valor recebem os valores correspondentes.  
  
 A implementação padrão de <xref:Microsoft.VisualStudio.Shell.DialogPage.SaveSettingsToXml%2A> usa a reflexão para descobrir propriedades públicas na <xref:Microsoft.VisualStudio.Shell.DialogPage> classe derivada e grava os nomes e valores de propriedade no feed XML como pares de nome-valor.  
  
### <a name="settings-category-registry-path"></a>Caminho do registro da categoria de configurações  
 O caminho do registro da categoria de configurações é determinado pela combinação <xref:Microsoft.VisualStudio.Shell.Package.ApplicationRegistryRoot%2A> , palavra, UserSettings, categoria de configurações e o nome do ponto de configurações personalizado. Os nomes da categoria de configurações e do ponto de configurações personalizadas são Unidos e separados por um sublinhado para formar o nome canônico e não localizado que aparece no registro. Por exemplo, se a categoria de configurações for "minha categoria", o nome do ponto de configurações personalizado "minhas configurações" e o ApplicationRegistryRoot HKEY_LOCAL_MACHINE \SOFTWARE\Microsoft\VisualStudio\8.0Exp, então a categoria de configurações terá a chave do registro, HKEY_LOCAL_MACHINE \SOFTWARE\Microsoft\VisualStudio\8.0Exp\UserSettings\My Category_My configurações.  
  
> [!NOTE]
> O nome canônico não aparece em uma interface do usuário. Ele é usado para associar um nome legível à categoria de configurações, muito parecida com um identificador programático (ProgID).  
  
### <a name="settings-category-attribute"></a>Atributo de categoria de configurações  
 O <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> determina o mapeamento de categorias para pontos de configurações personalizados no **Assistente de importação e exportação de configurações** , associando uma categoria ao VSPackage que a fornece. Considere o fragmento de código a seguir:  
  
 [!code-csharp[VSSDKSupportForSettingsCategories#1](../snippets/csharp/VS_Snippets_VSSDK/vssdksupportforsettingscategories/cs/vssdksupportforsettingscategoriespackage.cs#1)]
 [!code-vb[VSSDKSupportForSettingsCategories#1](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksupportforsettingscategories/vb/vssdksupportforsettingscategoriespackage.vb#1)]  
  
 A ID de recurso 106 é mapeada para "minha categoria", 107 para "minhas configurações" e 108 para "várias opções". Isso declara que `MyPackage` fornece a categoria, minhas configurações de Category_My. A categoria é fornecida pela `OptionsPageGeneral` classe, que deve implementar <xref:Microsoft.VisualStudio.Shell.IProfileManager> . As configurações nessa categoria são as propriedades públicas da `OptionsPageGeneral` classe.  
  
 No **Assistente de importação e exportação de configurações**, o ponto de configurações tem o nome, minhas configurações. Quando o ponto de configurações é selecionado, a descrição, **várias opções**, é exibida. O nome e a descrição do ponto de configurações são obtidos de recursos de cadeia de caracteres localizados.  
  
## <a name="see-also"></a>Consulte Também  
 [Criando uma página de opções](../extensibility/creating-an-options-page.md)   
 [Exemplos de VSSDK](../misc/vssdk-samples.md)   
 [Estado VSPackage](../misc/vspackage-state.md)   
 [Personalizando configurações de desenvolvimento no Visual Studio](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3)