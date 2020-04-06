---
title: Páginas de Opções e Opções | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Tools Options pages [Visual Studio SDK], managed package framework support
- managed package framework, Tools Options pages support
- support, Tools Options pages
- Tools Options pages [Visual Studio SDK], layouts
- Tools Options pages [Visual Studio SDK], attributes
ms.assetid: e6c0e636-5ec3-450e-b395-fc4bb9d75918
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7d21bf6d5ab7e23047a02e1188fff9a47d0cbd58
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80706833"
---
# <a name="options-and-options-pages"></a>Opções e páginas de opções
Clicar em **Opções** no menu **Ferramentas** abre a caixa de diálogo **Opções.** As opções nesta caixa de diálogo são coletivamente referidas como páginas de opções. O controle de árvore no painel de navegação inclui categorias de opções, e cada categoria tem páginas de opções. Quando você seleciona uma página, suas opções aparecem no painel direito. Essas páginas permitem alterar os valores das opções que determinam o estado de um VSPackage.

## <a name="support-for-options-pages"></a>Suporte para páginas de opções
 A <xref:Microsoft.VisualStudio.Shell.Package> classe oferece suporte para criar páginas de opções e categorias de opções. A <xref:Microsoft.VisualStudio.Shell.DialogPage> classe implementa uma página de opções.

 A implementação <xref:Microsoft.VisualStudio.Shell.DialogPage> padrão oferece suas propriedades públicas a um usuário em uma grade genérica de propriedades. Você pode personalizar esse comportamento substituindo vários métodos na página para criar uma página de opções personalizadas que tenha sua própria interface de usuário (Interface do Usuário). Para obter mais informações, consulte [Criando uma página de opções](../../extensibility/creating-an-options-page.md).

 A <xref:Microsoft.VisualStudio.Shell.DialogPage> classe <xref:Microsoft.VisualStudio.Shell.IProfileManager>implementa , o que fornece persistência para páginas de opções e também para configurações do usuário. As implementações padrão <xref:Microsoft.VisualStudio.Shell.IProfileManager.LoadSettingsFromStorage%2A> <xref:Microsoft.VisualStudio.Shell.IProfileManager.SaveSettingsToStorage%2A> dos métodos e métodos persistem alterações de propriedade em uma seção de usuário do registro se a propriedade pode ser convertida para e a partir de uma seqüência.

## <a name="options-page-registry-path"></a>Caminho de registro da página de opções
 Por padrão, o caminho de registro das propriedades gerenciadas <xref:Microsoft.VisualStudio.Shell.Package.UserRegistryRoot%2A>por uma página de opções é determinado combinando , a palavra DialogPage e o nome de tipo da classe de página de opções. Por exemplo, uma classe de página de opções pode ser definida da seguinte forma.

 [!code-csharp[VSSDKSupportForOptionsPages#1](../../extensibility/internals/codesnippet/CSharp/options-and-options-pages_1.cs)]
 [!code-vb[VSSDKSupportForOptionsPages#1](../../extensibility/internals/codesnippet/VisualBasic/options-and-options-pages_1.vb)]

 Se <xref:Microsoft.VisualStudio.Shell.Package.UserRegistryRoot%2A> o HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\8.0Exp, então os pares de nome e valor da propriedade são subchaves de HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\8.0Exp\DialogPage\Company.OptionsPage.OptionsPageGeneral.

 O caminho de registro da página de <xref:Microsoft.VisualStudio.Shell.Package.ApplicationRegistryRoot%2A>opções em si é determinado pela combinação , a palavra, ToolsOptionsPages e a categoria e nome da página de opções. Por exemplo, se a página de opções personalizadas <xref:Microsoft.VisualStudio.Shell.Package.ApplicationRegistryRoot%2A> tiver a categoria, Minhas Páginas de Opção e estiver HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp, a página de opções tem a chave de registro, HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp\ToolsOptionsPages\My Option Pages\Custom.

## <a name="toolsoptions-page-attributes-and-layout"></a>Atributos e layout da página ferramentas/opções
 O <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> atributo determina o agrupamento de páginas de opções personalizadas em categorias na árvore de navegação da caixa de diálogo **Opções.** O <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> atributo associa uma página de opções com o VSPackage que fornece a interface. Considere o fragmento de código a seguir:

 [!code-csharp[VSSDKSupportForOptionsPages#2](../../extensibility/internals/codesnippet/CSharp/options-and-options-pages_2.cs)]
 [!code-vb[VSSDKSupportForOptionsPages#2](../../extensibility/internals/codesnippet/VisualBasic/options-and-options-pages_2.vb)]

 Isso declara que o MyPackage fornece duas páginas de opções, OptionsPageGeneral e OptionsPageCustom. Na caixa de diálogo **Opções,** ambas as páginas de opções aparecem na categoria **Minhas páginas de opção** como **Geral** e **Personalizada,** respectivamente.

## <a name="option-attributes-and-layout"></a>Atributos de opção e layout
 A interface de usuário (UI) que a página fornece determina o aparecimento de opções em uma página de opções personalizadas. O layout, a rotulagem e a descrição das opções em uma página de opções genéricas são determinados pelos seguintes atributos:

- <xref:System.ComponentModel.CategoryAttribute>determina a categoria da opção.

- <xref:System.ComponentModel.DisplayNameAttribute>determina o nome de exibição da opção.

- <xref:System.ComponentModel.DescriptionAttribute>determina a descrição da opção.

  > [!NOTE]
  > Atributos equivalentes, SRCategory, LocDisplayName e SRDescription, usam recursos de string para localização e são definidos na [amostra de projeto gerenciado](/azure/devops/integrate/index).

  Considere o fragmento de código a seguir:

  [!code-csharp[VSSDKSupportForOptionsPages#3](../../extensibility/internals/codesnippet/CSharp/options-and-options-pages_3.cs)]
  [!code-vb[VSSDKSupportForOptionsPages#3](../../extensibility/internals/codesnippet/VisualBasic/options-and-options-pages_3.vb)]

  A opção OptionInteger aparece na página de opções como **Opção Inteiro** na categoria **Minhas opções.** Se a opção for selecionada, a **descrição, minha opção inteiro,** aparecerá na caixa de descrição.

## <a name="accessing-options-pages-from-another-vspackage"></a>Acessando páginas de opções de outro pacote VS
 Um VSPackage que hospeda e gerencia uma página de opções pode ser acessado de forma programática a partir de outro VSPackage usando o modelo de automação. Por exemplo, no código a seguir, um VSPackage é registrado como hospedagem de uma página de opção.

 [!code-csharp[VSSDKSupportForOptionsPages#4](../../extensibility/internals/codesnippet/CSharp/options-and-options-pages_4.cs)]
 [!code-vb[VSSDKSupportForOptionsPages#4](../../extensibility/internals/codesnippet/VisualBasic/options-and-options-pages_4.vb)]

 O fragmento de código a seguir obtém o valor de OptionInteger do MyOptionPage:

 [!code-csharp[VSSDKSupportForOptionsPages#5](../../extensibility/internals/codesnippet/CSharp/options-and-options-pages_5.cs)]
 [!code-vb[VSSDKSupportForOptionsPages#5](../../extensibility/internals/codesnippet/VisualBasic/options-and-options-pages_5.vb)]

 Quando <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> o atributo registra uma página de opções, a `SupportsAutomation` página é registrada `true`na tecla AutomationProperties se o argumento do atributo for . A automação examina esta entrada de registro para encontrar o VSPackage associado e, em seguida, acessa a propriedade através da página de opções hospedadas, neste caso, My Grid Page.

 O caminho de registro da propriedade <xref:Microsoft.VisualStudio.Shell.Package.ApplicationRegistryRoot%2A>de automação é determinado pela combinação , a palavra, AutomaçãoPropriedades e a categoria e nome da página de opções. Por exemplo, se a página de opções tiver a categoria <xref:Microsoft.VisualStudio.Shell.Package.ApplicationRegistryRoot%2A>Minha categoria, o nome da página Minha grade e o HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp, então a propriedade de automação tem a chave de registro, HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp\AutomationProperties\My Category\My Grid Page.

> [!NOTE]
> O nome canônico, My Category.My Grid Page, é o valor da subchave Nome desta chave.
