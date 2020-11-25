---
title: Página Aplicativo das propriedades de projeto do C#
description: Saiba como usar a página de aplicativo do designer de projeto C# para especificar as configurações e propriedades do aplicativo do projeto.
ms.custom: SEO-VS-2020
ms.date: 10/30/2018
ms.topic: reference
f1_keywords:
- cs.ProjectPropertiesApplicationWPF
- cs.ProjectPropertiesApplication
helpviewer_keywords:
- Project Designer, Application page
- Application page in Project Designer
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 0b77ee4edca8f9cb8de2079e01d9c9997a24aeff
ms.sourcegitcommit: 935e4d9a20928b733e573b6801a6eaff0d0b1b14
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/25/2020
ms.locfileid: "95871373"
---
# <a name="application-page-project-designer-c"></a>Página Aplicativo, Designer de Projeto (C#)

Use a página **Aplicativo** do **Designer de Projeto** para especificar as propriedades e configurações de aplicativo do projeto.

Para acessar a página **Aplicativo**, escolha um nó de projeto (não o nó **Solução**) no **Gerenciador de Soluções**. Em seguida, escolha Propriedades do **projeto**  >  **Properties** na barra de menus. Quando o **Designer de Projeto** for exibido, clique na guia **Aplicativo**.

[!INCLUDE[note_settings_general](../../data-tools/includes/note_settings_general_md.md)]

## <a name="general-application-settings"></a>Configurações Gerais de Aplicativos

As opções a seguir permitem definir as configurações gerais para o aplicativo.

**Nome do assembly**

Especifica o nome do arquivo de saída que guardará o manifesto do assembly. Alterar essa propriedade também altera a propriedade **Nome de saída**.

Também é possível fazer essa alteração na linha de comando usando [/out (opções do compilador C#)](/dotnet/csharp/language-reference/compiler-options/out-compiler-option).

Para acessar essa propriedade de forma programática, consulte <xref:VSLangProj.ProjectProperties.AssemblyName%2A>.

**Namespace padrão**

Especifica o namespace base para arquivos adicionados ao projeto.

Consulte [namespace](/dotnet/csharp/language-reference/keywords/namespace) para obter mais informações sobre a criação de namespaces em seu código.

Para acessar essa propriedade de forma programática, consulte <xref:VSLangProj.ProjectProperties.RootNamespace%2A>.

**Estrutura de destino**

Especifica a versão do .NET direcionada pelo aplicativo. Essa opção pode ter valores diferentes dependendo de quais versões do .NET estão instaladas no computador.

Para projetos .NET Framework, o valor padrão corresponde à estrutura de destino que você especificou quando criou o projeto.

Para um projeto direcionado ao .NET Core, as versões disponíveis poderão ser exibidas da seguinte maneira:

![Versões da estrutura de destino para um projeto .NET Core](../media/application-target-framework.png)

> [!NOTE]
> Os pacotes de pré-requisitos listados na [Caixa de diálogo Pré-requisitos](../../ide/reference/prerequisites-dialog-box.md) são definidos automaticamente na primeira vez em que a caixa de diálogo é aberta. Se você alterar posteriormente a estrutura de destino do projeto, será necessário selecionar os pré-requisitos manualmente para corresponder à nova estrutura de destino.

Para obter mais informações, confira [Visão geral do direcionamento de estrutura](../../ide/visual-studio-multi-targeting-overview.md).

**Tipo de saída**

Especifica o tipo de aplicativo a ser compilado. Os valores são diferentes dependendo do tipo de projeto. Por exemplo, para um projeto do **Aplicativo de Console**, é possível especificar **Aplicativo do Windows**, **Aplicativo de Console** ou **Biblioteca de Classes** como o tipo de saída.

Para um projeto de aplicativo Web, é necessário especificar **Biblioteca de Classes**.

Para obter mais informações sobre a propriedade **Tipo de saída**, confira [/target (Opções do compilador do C#)](/dotnet/csharp/language-reference/compiler-options/target-compiler-option).

Para obter informações sobre como acessar esta propriedade de forma programática, consulte <xref:VSLangProj.ProjectProperties.OutputType%2A>.

**Gerar redirecionamentos de associação automaticamente**

Os redirecionamentos da associação serão adicionados ao seu projeto se o aplicativo ou seus componentes referenciarem mais de uma versão do mesmo assembly. Se você desejar definir manualmente os redirecionamentos de associação no arquivo de projeto, desmarque **Gerar Redirecionamentos de Associação Automaticamente**.

Para obter mais informações sobre o redirecionamento, confira [Redirecionando versões de assembly](/dotnet/framework/configure-apps/redirect-assembly-versions).

**Objeto de inicialização**

Define o ponto de entrada a ser chamado quando o aplicativo é carregado. Geralmente, isso é definido como o principal formulário em seu aplicativo ou como o procedimento `Main` que deve ser executado quando o aplicativo é iniciado. Como as bibliotecas de classes não têm um ponto de entrada, sua única opção para essa propriedade é **(Não definido)**.

Por padrão, em um projeto do aplicativo WPF, esta opção é definida como **(Não definido)**. A outra opção é \[nomedoprojeto].App. Em um projeto do WPF, é necessário definir o URI de inicialização para carregar um recurso de interface do usuário quando o aplicativo é iniciado. Para fazer isso, abra o arquivo *Application.xaml* em seu projeto e defina a propriedade `StartupUri` como um arquivo *.xaml* em seu projeto, como *Window1.xaml*. Para obter uma lista dos elementos raiz aceitáveis, consulte <xref:System.Windows.Application.StartupUri%2A>. Também é necessário definir um método `public static void Main()` em uma classe no projeto. Essa classe será exibida na lista **Objeto de inicialização** como *ProjectName.ClassName*. Em seguida, é possível selecionar a classe como o objeto de inicialização.

Consulte [/main (Opções do compilador do C#)](/dotnet/csharp/language-reference/compiler-options/main-compiler-option) para obter mais informações. Para acessar essa propriedade de forma programática, consulte <xref:VSLangProj.ProjectProperties.StartupObject%2A>.

**Informações do assembly**

Esse botão abre a caixa de diálogo [Informações do assembly](../../ide/reference/assembly-information-dialog-box.md).

## <a name="resources"></a>Recursos

As opções **Recursos** ajudam a definir as configurações de recursos para seu aplicativo.

**Ícone e manifesto**

Por padrão, este botão de opção é selecionado e as opções **Ícone** e **Manifesto** são habilitadas. Isso permite selecionar seu próprio ícone ou diferentes opções de geração de manifesto. Deixe esse botão de opção selecionado, a menos que você esteja fornecendo um arquivo de recurso para o projeto.

**Ícone**

Define o arquivo *.ico* que você deseja usar como seu ícone do programa. Clique em **Procurar** para procurar um gráfico existente ou digite o nome do arquivo que você deseja. Consulte [-win32icon](/dotnet/csharp/language-reference/compiler-options/win32icon-compiler-option) (Opções do compilador do C#) para obter mais informações.

Para acessar essa propriedade de forma programática, consulte <xref:VSLangProj.ProjectProperties.ApplicationIcon%2A>.

Para obter informações sobre como criar um ícone, confira [Editor de imagens para ícones](/cpp/windows/image-editor-for-icons).

**Manifesto**

Seleciona uma opção de geração de manifesto quando o aplicativo é executado no Windows Vista no UAC (Controle de Conta de Usuário). Essa opção pode ter os seguintes valores:

- **Inserir manifesto com configurações padrão**. Dá suporte à maneira típica como o Visual Studio funciona no Windows Vista, que é inserir as informações de segurança no arquivo executável do aplicativo, especificando que `requestedExecutionLevel` seja `AsInvoker`. Essa é a opção padrão.

- **Criar aplicativo sem um manifesto**. Esse método é conhecido como *virtualização*. Use essa opção para compatibilidade com aplicativos anteriores.

- **Properties\app.manifest**. Essa opção é necessária para aplicativos implantados pelo ClickOnce ou COM sem registro. Se você publicar um aplicativo usando a implantação do ClickOnce, **Manifesto** será definido automaticamente como essa opção.

**Arquivo de recurso**

Selecione esse botão de opção quando você estiver fornecendo um arquivo de recurso para o projeto. Selecionar essa opção desabilita as opções **Ícone** e **Manifesto**.

Insira um nome de caminho ou use o botão Procurar (**...**) para adicionar um arquivo de recurso Win32 ao projeto.

Para obter mais informações, confira [Criar arquivos de recurso para aplicativos .NET](/dotnet/framework/resources/creating-resource-files-for-desktop-apps).
