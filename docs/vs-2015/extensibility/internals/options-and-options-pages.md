---
title: Opções e páginas de opções | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Tools Options pages [Visual Studio SDK], managed package framework support
- managed package framework, Tools Options pages support
- support, Tools Options pages
- Tools Options pages [Visual Studio SDK], layouts
- Tools Options pages [Visual Studio SDK], attributes
ms.assetid: e6c0e636-5ec3-450e-b395-fc4bb9d75918
caps.latest.revision: 35
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 4512867f636e2362aa28d52c5af28bf8eb9697f9
ms.sourcegitcommit: c150d0be93b6f7ccbe9625b41a437541502560f5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/10/2020
ms.locfileid: "75851158"
---
# <a name="options-and-options-pages"></a>Opções e páginas de opções
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Clicar em **Opções** no menu **ferramentas** abre a caixa de diálogo **Opções** . As opções nessa caixa de diálogo são chamadas coletivamente de páginas de opções. O controle de árvore no painel de navegação inclui categorias de opções e cada categoria tem páginas de opções. Quando você seleciona uma página, suas opções aparecem no painel direito. Essas páginas permitem que você altere os valores das opções que determinam o estado de um VSPackage.  
  
## <a name="support-for-options-pages"></a>Suporte para páginas de opções  
 A classe <xref:Microsoft.VisualStudio.Shell.Package> fornece suporte para a criação de categorias de opções páginas e opções. A classe <xref:Microsoft.VisualStudio.Shell.DialogPage> implementa uma página de opções.  
  
 A implementação padrão de <xref:Microsoft.VisualStudio.Shell.DialogPage> oferece suas propriedades públicas para um usuário em uma grade genérica de propriedades. Você pode personalizar esse comportamento substituindo vários métodos na página para criar uma página de opções personalizadas que tenha sua própria interface do usuário. Para obter mais informações, consulte [criando uma página de opções](../../extensibility/creating-an-options-page.md).  
  
 A classe <xref:Microsoft.VisualStudio.Shell.DialogPage> implementa <xref:Microsoft.VisualStudio.Shell.IProfileManager>, que fornece persistência para páginas de opções e também para configurações de usuário. As implementações padrão dos métodos <xref:Microsoft.VisualStudio.Shell.IProfileManager.LoadSettingsFromStorage%2A> e <xref:Microsoft.VisualStudio.Shell.IProfileManager.SaveSettingsToStorage%2A> manterão as alterações de propriedade em uma seção de usuário do registro se a propriedade puder ser convertida em e de uma cadeia de caracteres.  
  
## <a name="options-page-registry-path"></a>Caminho do registro da página de opções  
 Por padrão, o caminho do registro das propriedades gerenciadas por uma página de opções é determinado pela combinação de <xref:Microsoft.VisualStudio.Shell.Package.UserRegistryRoot%2A>, da palavra DialogPage e do nome do tipo da classe de página de opções. Por exemplo, uma classe de página de opções pode ser definida da seguinte maneira.  
  
 [!code-csharp[VSSDKSupportForOptionsPages#1](../../snippets/csharp/VS_Snippets_VSSDK/vssdksupportforoptionspages/cs/vssdksupportforoptionspagespackage.cs#1)]
 [!code-vb[VSSDKSupportForOptionsPages#1](../../snippets/visualbasic/VS_Snippets_VSSDK/vssdksupportforoptionspages/vb/vssdksupportforoptionspagespackage.vb#1)]  
  
 Se a <xref:Microsoft.VisualStudio.Shell.Package.UserRegistryRoot%2A> for HKEY_CURRENT_USER \Software\Microsoft\VisualStudio\8.0Exp, os pares nome da propriedade e valor serão subchaves de HKEY_CURRENT_USER \Software\Microsoft\VisualStudio\8.0Exp\DialogPage\Company.OptionsPage.OptionsPageGeneral.  
  
 O caminho do registro da própria página de opções é determinado pela combinação de <xref:Microsoft.VisualStudio.Shell.Package.ApplicationRegistryRoot%2A>, a palavra, ToolsOptionsPages e a categoria e o nome da página de opções. Por exemplo, se a página opções personalizadas tiver a categoria, as páginas de minha opção e a <xref:Microsoft.VisualStudio.Shell.Package.ApplicationRegistryRoot%2A> for HKEY_LOCAL_MACHINE \SOFTWARE\Microsoft\VisualStudio\8.0Exp, a página opções terá a chave do registro, HKEY_LOCAL_MACHINE opção \SOFTWARE\Microsoft\VisualStudio\8.0Exp\ToolsOptionsPages\My Pages\Custom.  
  
## <a name="toolsoptions-page-attributes-and-layout"></a>Layout e atributos de página de ferramentas/opções  
 O atributo <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> determina o agrupamento de páginas de opções personalizadas em categorias na árvore de navegação da caixa de diálogo **Opções** . O atributo <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> associa uma página de opções com o VSPackage que fornece a interface. Considere o fragmento de código a seguir:  
  
 [!code-csharp[VSSDKSupportForOptionsPages#2](../../snippets/csharp/VS_Snippets_VSSDK/vssdksupportforoptionspages/cs/vssdksupportforoptionspagespackage.cs#2)]
 [!code-vb[VSSDKSupportForOptionsPages#2](../../snippets/visualbasic/VS_Snippets_VSSDK/vssdksupportforoptionspages/vb/vssdksupportforoptionspagespackage.vb#2)]  
  
 Isso declara que MyPackage fornece duas páginas de opções, OptionsPageGeneral e OptionsPageCustom. Na caixa de diálogo **Opções** , ambas as páginas de opções aparecem na categoria de **páginas minha opção** , como **geral** e **personalizada**, respectivamente.  
  
## <a name="option-attributes-and-layout"></a>Layout e atributos de opção  
 A interface do usuário (IU) que a página fornece determina a aparência das opções em uma página de opções personalizadas. O layout, a rotulagem e a descrição das opções em uma página de opções genéricas são determinados pelos seguintes atributos:  
  
- <xref:System.ComponentModel.CategoryAttribute> determina a categoria da opção.  
  
- <xref:System.ComponentModel.DisplayNameAttribute> determina o nome de exibição da opção.  
  
- <xref:System.ComponentModel.DescriptionAttribute> determina a descrição da opção.  
  
  > [!NOTE]
  > Atributos equivalentes, SRCategory, LocDisplayName e SRDescription, usam recursos de cadeia de caracteres para localização e são definidos no [exemplo de projeto gerenciado](https://msdn.com/vsx).  
  
  Considere o fragmento de código a seguir:  
  
  [!code-csharp[VSSDKSupportForOptionsPages#3](../../snippets/csharp/VS_Snippets_VSSDK/vssdksupportforoptionspages/cs/optionspagecustom.cs#3)]
  [!code-vb[VSSDKSupportForOptionsPages#3](../../snippets/visualbasic/VS_Snippets_VSSDK/vssdksupportforoptionspages/vb/optionspagegeneral.vb#3)]  
  
  A opção OptionInteger aparece na página opções como **opção de inteiro** na categoria **minhas opções** . Se a opção estiver selecionada, a opção descrição, **meu inteiro**aparecerá na caixa Descrição.  
  
## <a name="accessing-options-pages-from-another-vspackage"></a>Acessando páginas de opções de outro VSPackage  
 Um VSPackage que hospeda e gerencia uma página de opções pode ser acessado por meio de programação de outro VSPackage usando o modelo de automação. Por exemplo, no código a seguir, um VSPackage é registrado como Hospedagem de uma página de opções.  
  
 [!code-csharp[VSSDKSupportForOptionsPages#4](../../snippets/csharp/VS_Snippets_VSSDK/vssdksupportforoptionspages/cs/vssdksupportforoptionspagespackage.cs#4)]
 [!code-vb[VSSDKSupportForOptionsPages#4](../../snippets/visualbasic/VS_Snippets_VSSDK/vssdksupportforoptionspages/vb/vssdksupportforoptionspagespackage.vb#4)]  
  
 O fragmento de código a seguir obtém o valor de OptionInteger de MyOptionPage:  
  
 [!code-csharp[VSSDKSupportForOptionsPages#5](../../snippets/csharp/VS_Snippets_VSSDK/vssdksupportforoptionspages/cs/vssdksupportforoptionspagespackage.cs#5)]
 [!code-vb[VSSDKSupportForOptionsPages#5](../../snippets/visualbasic/VS_Snippets_VSSDK/vssdksupportforoptionspages/vb/vssdksupportforoptionspagespackage.vb#5)]  
  
 Quando o atributo <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> registra uma página de opções, a página é registrada na chave AutomationProperties se o argumento `SupportsAutomation` do atributo for `true`. A automação examina essa entrada de registro para localizar o VSPackage associado e a automação, em seguida, acessa a propriedade por meio da página opções hospedadas, nesse caso, a página de grade.  
  
 O caminho do registro da propriedade de automação é determinado pela combinação de <xref:Microsoft.VisualStudio.Shell.Package.ApplicationRegistryRoot%2A>, a palavra, a AutomationProperties e a categoria e o nome da página de opções. Por exemplo, se a página de opções tiver a categoria minha categoria, o nome da página de grade e o <xref:Microsoft.VisualStudio.Shell.Package.ApplicationRegistryRoot%2A>, HKEY_LOCAL_MACHINE \SOFTWARE\Microsoft\VisualStudio\8.0Exp, a propriedade de automação terá a chave do registro, HKEY_LOCAL_MACHINE página de grade do \SOFTWARE\Microsoft\VisualStudio\8.0Exp\AutomationProperties\My Category\My.  
  
> [!NOTE]
> O nome canônico, minha página de grade Category.My, é o valor da subchave Name dessa chave.
