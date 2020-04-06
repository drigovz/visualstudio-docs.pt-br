---
title: Começando com o modelo do projeto VSIX | Microsoft Docs
ms.date: 3/16/2019
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio SDK, VSIX project template
ms.assetid: 89fac33e-9380-4723-9b45-048a6e16f0ed
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 773e9e6891599cd9672888d0521e94891e0d9f41
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80711243"
---
# <a name="get-started-with-the-vsix-project-template"></a>Comece com o modelo do Projeto VSIX

Você pode usar o modelo do Projeto VSIX para criar uma extensão ou para empacotar uma extensão existente para implantação. O modelo do Projeto VSIX tem versões Visual Basic e Visual C#, e está instalado como parte do Visual Studio SDK.

 O modelo do Projeto VSIX consiste apenas em um arquivo *source.extension.vsixmanifest,* que contém informações sobre a extensão e os ativos que ele envia.

 Para encontrar o modelo de projeto VSIX, você deve instalar o Visual Studio SDK. Para obter mais informações, consulte [Visual Studio SDK](../extensibility/visual-studio-sdk.md).

## <a name="deploy-a-custom-project-template-using-the-vsix-project-template"></a>Implantar um modelo de projeto personalizado usando o modelo do Projeto VSIX

 As etapas a seguir mostram como usar o projeto VSIX para empacotar um modelo de projeto que você pode compartilhar com outros desenvolvedores ou fazer upload para a Visual Studio Gallery.

1. Crie um modelo de projeto.

    1. Abra o projeto a partir do qual criar um modelo. Este projeto pode ser de qualquer tipo de projeto.

    2. No menu **Projeto**, clique em **Exportar Modelo**. Complete os passos do mago.

         Um arquivo *.zip* é criado em *%USERPROFILE%\Meus Documentos\Visual Studio {versão}\Meus modelos\\exportados*.

2. Crie um projeto VSIX vazio.

     Selecione **Arquivo** > **Novo** > **Projeto**. Na caixa de pesquisa, digite "vsix" e selecione a versão **C#** ou **Visual Basic** do **Projeto VSIX**.

3. Adicione o arquivo *.zip* ao projeto. Defina sua propriedade Copiar `Copy Always`para Diretório **de** saída para .

4. No **Solution Explorer,** clique duas vezes no arquivo *source.extension.vsixmanifest* para abri-lo no **VSIX Manifest Designer**e, em seguida, faça as seguintes alterações:

    - Defina o **campo Nome do Produto** como Modelo do Meu **Projeto**.

    - Defina o **campo ID do produto** como **MyProjectTemplate - 1**.

    - Defina o campo **Autor** para **Fabrikam**.

    - Defina o campo **Descrição** no **meu modelo de projeto**.

    - Na seção **Ativos,** adicione um tipo **Microsoft.VisualStudio.ProjectTemplate** e defina seu caminho para o nome do arquivo *.zip.*

5. Salvar e fechar o arquivo *source.extension.vsixmanifest.*

6. Compile o projeto.

7. No diretório de saída, clique duas vezes no arquivo *.vsix.*

8. Uma caixa de mensagem **do Instalador VSIX** é exibida. Siga as instruções para instalar a extensão.

9. Feche o Visual Studio e, em seguida, o reabra.

::: moniker range="vs-2017"

10. Selecione **Extensões e Atualizações** (no menu **Ferramentas)** e selecione a categoria **Modelos.** Uma das extensões disponíveis deve ser **O Modelo do Meu Projeto**.

::: moniker-end

::: moniker range=">=vs-2019"

10. Selecione **Gerenciar extensões** (no menu **Extensões)** e selecione a categoria **Modelos.** Uma das extensões disponíveis deve ser **O Modelo do Meu Projeto**.

::: moniker-end

11. O novo modelo de projeto aparece no diálogo **Novo Projeto** no mesmo lugar do modelo original do projeto. Por exemplo, se você criou um modelo chamado **VB Console** a partir de um aplicativo de console Visual Basic, o **VB Console** aparecerá no mesmo painel do modelo Visual Basic **Console Application.**

### <a name="to-specify-the-location-of-the-template-in-the-new-project-dialog-box"></a>Para especificar a localização do modelo na caixa Diálogo novo projeto

1. As pastas de modelo estão localizadas nos diretórios *{Visual Studio Installation Path}\Common7\IDE\ProjectTemplates* e *{Visual Studio Installation Path}\Common7\IDE\ItemTemplates.* Os nomes das seções de nível superior na caixa de diálogo **Novo Projeto** não correspondem exatamente aos nomes das pastas de modelo. Quando eles diferem, use o nome da pasta de modelo.

    Altere a extensão de arquivo *.vsix* para *.zip*e, em seguida, abra o arquivo.

2. Crie uma nova pasta com o mesmo nome da seção da caixa de diálogo **Novo Projeto** em que o modelo deve aparecer.

3. Se o modelo for aparecer em uma subseção, crie uma subpasta com o mesmo nome.

4. Mova o arquivo *modelo .zip* para a nova pasta.

5. Altere a extensão *.zip* para *.vsix*.

6. Abra o manifesto VSIX.

7. No manifesto VSIX, atualize o caminho **De ativos** do modelo para que ele aponte para a raiz da árvore de diretório que contém o arquivo de modelo. Por exemplo, se o modelo estiver em *\CSharp\Windows,* a referência deve apontar para *\CSharp*.
