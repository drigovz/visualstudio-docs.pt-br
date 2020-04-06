---
title: Criar um pacote de extensão com o modelo de item do pacote de extensão | Microsoft Docs
ms.date: 07/27/2018
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - extensions
ms.assetid: 5388EEBA-211D-4114-8CD9-70C899919F7E
author: acangialosi
ms.author: anthc
manager: Meng
ms.workload:
- vssdk
ms.openlocfilehash: fa1c141e18a3870eaad4b155d816e30ee207f45d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80697744"
---
# <a name="walkthrough-create-an-extension-pack"></a>Passo a passo: criar um pacote de extensão

Um Pacote de Extensão é um conjunto de extensões que podem ser instaladas em conjunto. Os Pacotes de extensão permitem que você compartilhe facilmente suas extensões favoritas com outros usuários ou junte um conjunto de extensões para um cenário específico.

## <a name="prerequisites"></a>Pré-requisitos

A partir do Visual Studio 2015, o Visual Studio SDK está incluído como um recurso opcional na configuração do Visual Studio. Você também pode instalar o VS SDK mais tarde. Para obter mais informações, consulte [Instalando o Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).

O recurso Extension Pack está disponível a partir do Visual Studio 15.8 Preview 2.

## <a name="create-an-extension-with-an-extension-pack-item-template"></a>Crie uma extensão com um modelo de item do Extension Pack

O modelo de item Extension Pack cria um Pacote de Extensão com conjunto de extensões que podem ser instaladas juntas.

1. Na caixa de diálogo **Novo Projeto,** procure por "vsix" e selecione **Projeto VSIX**. Para **nome do projeto,** digite "Test Extension Pack". Selecione **Criar**.

2. No **Solution Explorer,** clique com o botão direito do mouse no nó do projeto e **selecione Adicionar** > **novo item**. Vá para o nó de **extensibilidade** Visual C# e selecione **Pacote de extensão**. Deixe o nome do arquivo padrão (ExtensionPack1.cs).

3. O arquivo ExtensionPack1.vsext é adicionado que contém o seguinte código

   ```json
   {
    "id": "ExtensionPack1",
    "name": "ExtensionPack1",
    "description": "Read about creating extension packs at https://aka.ms/vsextpack",
    "version": "1.0.0.0",
    "extensions": [  // List of extensions that are included in the Extension Pack.
      {
        "vsixId": "41858b2d-ff0b-4a43-80b0-f1b2d6084935", // The vsix id of the extension you want to   include.
        "name": "AlignAssignments"
      },
      {
          "vsixId": "42374550-426a-400e-96f9-237682e8dea6",
        "name": "CopyAsHtml"
      }
    ]
   }
   ```

4. O vsixide da extensão a ser incluida no Pacote de Extensão pode ser encontrado no [Visual Studio Marketplace](https://marketplace.visualstudio.com/). Encontre a extensão que deseja incluir e clique em **Copiar ID**. Você pode atualizar o **vsixId** existente no arquivo acima ou adicionar outra extensão à lista.

    ![Copiar VsixId do Marketplace](media/vsixid-marketplace.png)

5. Construa o projeto e carregue sua extensão para o Marketplace. Consulte [Publicando uma extensão do Visual Studio](../extensibility/walkthrough-publishing-a-visual-studio-extension.md).

> [!NOTE]
> Um pacote de extensão só pode instalar extensões disponíveis no [Visual Studio Marketplace](https://marketplace.visualstudio.com/) ou na galeria [Private](../extensibility/how-to-create-an-atom-feed-for-a-private-gallery.md).

## <a name="install-the-extension-pack-from-the-visual-studio-marketplace"></a>Instale o pacote de extensão do Visual Studio Marketplace

Agora que a extensão foi publicada, instale-a no Visual Studio e teste-a lá.

::: moniker range="vs-2017"

1. No Visual Studio, no menu **Ferramentas,** clique em **Extensões e Atualizações**.

::: moniker-end

::: moniker range=">=vs-2019"

1. No Visual Studio, no menu **Extensões,** clique em **Extensões gerenciadas**.

::: moniker-end

2. Clique **em Online** e, em seguida, procure por "Pacote de extensão de teste".

3. Clique em **Download**. A extensão e sua lista de extensões incluídas no Pacote de Extensão serão então agendadas para instalação.

4. Abaixo está uma exibição de download do Pacote de Extensão de exemplo da caixa de diálogo **Gerenciar extensões.** Se você preferir instalar apenas algumas das extensões incluídas no pacote extensão, você pode modificar a lista de extensões em **Scheduled For Install**.

    ![Baixar pacote de extensão do marketplace](media/vside-extensionpack.png)

5. Para concluir a instalação, feche todas as instâncias do Visual Studio.

## <a name="remove-the-extension"></a>Remover a extensão

Para remover a extensão do seu computador:

::: moniker range="vs-2017"

1. No Visual Studio, no menu **Ferramentas,** clique em **Extensões e Atualizações**.

::: moniker-end

::: moniker range=">=vs-2019"

1. No Visual Studio, no menu **Extensões,** clique em **Extensões gerenciadas**.

::: moniker-end

2. Selecione **'Pacote de extensão de teste'** e clique **em Desinstalar**. A extensão e sua lista de extensões incluídas no Pacote de Extensão serão então agendadas para desinstalação.

3. Para concluir a desinstalação, feche todas as instâncias do Visual Studio.
