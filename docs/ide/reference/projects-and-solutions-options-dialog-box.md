---
title: Projetos e Soluções, caixa de diálogo Opções
ms.date: 07/26/2019
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Projects.General
helpviewer_keywords:
- Projects and Solutions Options dialog box
- Options dialog box, Projects and Solutions
ms.assetid: 2801f24e-a138-488a-ae3c-e1f99a678ac0
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 1ed60e07c625665f92838cfbc671b03c605fda0d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "75567639"
---
# <a name="options-dialog-box-projects-and-solutions--general"></a>Caixa de diálogo opções: projetos e soluções \> geral

Use esta página para definir o comportamento do Visual Studio relacionado a projetos e soluções. Para acessar essas opções, selecione **ferramentas**  >  **Opções**, expanda **projetos e soluções**e, em seguida, selecione **geral**.

As seguintes opções estão disponíveis na página **Geral**.

## <a name="always-show-error-list-if-build-finishes-with-errors"></a>Sempre mostrar a Lista de Erros se o build for concluído com erros

Abre a janela **Lista de Erros** após a conclusão do build, somente se houve falha de build de um projeto. Os erros que ocorrem durante o processo de build são exibidos. Quando essa opção estiver desmarcada, os erros ainda ocorrerão, mas a janela não será aberta quando o build for concluído. Essa opção é habilitada por padrão.

## <a name="track-active-item-in-solution-explorer"></a>Acompanhar item ativo no Gerenciador de Soluções

Quando essa opção estiver selecionada, o **Gerenciador de Soluções** será aberto automaticamente e o item ativo será selecionado. O item selecionado é alterado conforme você trabalha com arquivos diferentes em um projeto ou uma solução, ou com componentes diferentes em um designer. Quando essa opção estiver desmarcada, a seleção no **Gerenciador de Soluções** não será alterada automaticamente. Essa opção é habilitada por padrão.

## <a name="show-advanced-build-configurations"></a>Mostrar configurações de build avançadas

Quando estiverem marcadas, as opções de configuração de build serão exibidas nas caixas de diálogo **Páginas de Propriedades do Projeto** e **Páginas de Propriedades da Solução**. Quando desmarcada, as opções de configuração de build não aparecem nas caixas de diálogo **Páginas de Propriedades do Projeto** e **Páginas de Propriedade da Solução** para projetos do Visual Basic e do C# que contêm uma configuração ou as duas configurações de depuração e versão. Se um projeto tiver uma configuração definida pelo usuário, as opções de configuração de build serão mostradas.

Quando estiverem desmarcados, os comandos do menu **Build**, como **Compilar Solução**, **Recompilar Solução** e **Limpar Solução** serão executados na configuração de Versão e os comandos do menu **Depurar**, como **Iniciar Depuração** e **Iniciar Sem Depuração**, serão executados na configuração de Depuração.

## <a name="always-show-solution"></a>Sempre mostrar solução

Quando essa opção estiver selecionada, a solução e todos os comandos que atuam em soluções sempre serão mostrados no IDE. Quando estiver desmarcada, todos os projetos serão criados como projetos independentes e você não verá a solução no Gerenciador de Soluções nem os comandos que atuam em soluções no IDE se a solução contiver apenas um projeto.

::: moniker range="vs-2017"

## <a name="save-new-projects-when-created"></a>Salvar novos projetos quando criados

Quando essa opção estiver selecionada, será possível especificar um local para o projeto na caixa de diálogo **Novo Projeto**. Quando estiver desmarcada, todos os novos projetos serão criados como projetos temporários. Quando você estiver trabalhando com projetos temporários, poderá criar e testar um projeto sem a necessidade de especificar um local de disco.

::: moniker-end

## <a name="warn-user-when-the-project-location-is-not-trusted"></a>Avisar o usuário quando o local do projeto não é confiável

Se você tentar criar um novo projeto ou abrir um projeto existente em um local que não é totalmente confiável (por exemplo, em um caminho UNC ou um caminho HTTP), uma mensagem será exibida. Use essa opção para especificar se a mensagem será exibida sempre que você tentar criar ou abrir um projeto em um local que não é totalmente confiável.

## <a name="show-output-window-when-build-starts"></a>Mostrar a Janela de Saída quando o build é iniciado

Exibe automaticamente a [janela de saída](../../ide/reference/output-window.md) no IDE no início das compilações da solução.

## <a name="prompt-for-symbolic-renaming-when-renaming-files"></a>Prompt para renomeação simbólica ao renomear arquivos

Quando selecionada, o Visual Studio exibe uma caixa de mensagem perguntando se ele também deve renomear todas as referências no projeto com o elemento de código.

## <a name="prompt-before-moving-files-to-a-new-location"></a>Prompt antes de mover arquivos para um novo local

Quando selecionada, o Visual Studio exibe uma caixa de mensagem de confirmação antes que os locais de arquivos sejam alterados pelas ações no **Gerenciador de Soluções**.

## <a name="reopen-documents-on-solution-load"></a>Reabrir documentos no carregamento da solução

Quando selecionada, os documentos que foram deixados abertos na última vez em que a solução foi fechada são abertos automaticamente quando a solução é aberta.

Reabrir certos tipos de arquivos ou designers pode atrasar o carregamento da solução. Desmarque essa opção para [melhorar o desempenho de carregamento da solução](../../ide/visual-studio-performance-tips-and-tricks.md#disable-automatic-file-restore) se você não quiser restaurar o contexto anterior da solução.

::: moniker range=">=vs-2019"

## <a name="restore-solution-explorer-project-hierarchy-state-on-solution-load"></a>Restaurar o estado da hierarquia do projeto do Gerenciador de Soluções após o carregamento da solução

Quando selecionada, essa opção restaura o estado dos nós no Gerenciador de Soluções com relação a se eles foram expandidos ou recolhidos na última vez em que a solução foi aberta. Desmarque essa opção para diminuir o tempo de carregamento de soluções grandes.

> [!TIP]
> Se você desabilitar essa opção, uma maneira fácil de navegar até o documento ativo no Gerenciador de Soluções será selecionar a opção **Sincronizar com Documento Ativo** na barra de ferramentas do **Gerenciador de Soluções**.
>
> ![Sincronizar com documento ativo no Gerenciador de Soluções](media/sync-active-document.png)

## <a name="open-sdk-style-project-files-with-double-click-or-the-enter-key"></a>Abrir arquivos de projeto no estilo do SDK com o clique duplo ou a tecla Enter

Quando essa opção é selecionada e você clica duas vezes em um nó de projeto no estilo do SDK no Gerenciador de Soluções ou seleciona-o e pressiona **Enter**, o arquivo de projeto (por exemplo, arquivo \*.csproj) é aberto como XML no editor. Quando essa opção é desmarcada, clicar duas vezes em um nó de projeto no estilo do SDK no Gerenciador de Soluções ou selecioná-lo e pressionar **Enter** tem o efeito de expandir ou recolher apenas o nó.

Se você não tiver essa opção selecionada e desejar editar um arquivo de projeto no estilo do SDK, clique com o botão direito do mouse no nó do projeto no Gerenciador de Soluções e selecione **Editar Arquivo de Projeto**. Para outros tipos de projeto, é necessário primeiro descarregar o projeto antes de editá-lo no Visual Studio.

> [!TIP]
> Um *projeto no estilo do SDK* ou um [SDK do projeto](../../msbuild/how-to-use-project-sdk.md) tem um formato de arquivo de projeto mais novo e simplificado que foi introduzido no MSBuild 15.0. Um projeto no estilo do SDK contém um atributo `Sdk` no elemento `Project`, por exemplo, `<Project Sdk="Microsoft.NET.Sdk">`. O Visual Studio cria um projeto no estilo do SDK quando você cria um projeto .NET Core com base em um dos modelos do Visual Studio, por exemplo.

::: moniker-end

## <a name="see-also"></a>Confira também

- [Caixa de diálogo opções: locais de projetos e soluções \>](projects-solutions-locations-options.md)
- [Caixa de diálogo Opções, Projetos e Soluções, Compilar e Executar](../../ide/reference/options-dialog-box-projects-and-solutions-build-and-run.md)
- [Caixa de diálogo Opções, Projetos e Soluções, Projetos Web](../../ide/reference/options-dialog-box-projects-and-solutions-web-projects.md)
