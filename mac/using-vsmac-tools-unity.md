---
title: Usando as Ferramentas do Visual Studio para Mac para Unity
description: Este guia descreve como usar a extensão das Ferramentas do Visual Studio para Mac para Unity
author: therealjohn
ms.author: johmil
ms.date: 12/13/2019
ms.assetid: 83FDD7A3-5D16-4B4B-9080-078E3FB5C623
ms.openlocfilehash: 4247e5cfb936d79c2b2bea5ac68a16164f0c0ef0
ms.sourcegitcommit: 8e123bcb21279f2770b28696995450270b4ec0e9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/25/2019
ms.locfileid: "75406666"
---
# <a name="using-visual-studio-for-mac-tools-for-unity"></a>Usando as Ferramentas do Visual Studio para Mac para Unity

Nesta seção, você aprenderá como usar os recursos de integração e produtividade das Ferramentas do Visual Studio para Mac para Unity e como usar o depurador do Visual Studio para Mac para desenvolvimento no Unity.

## <a name="opening-unity-scripts-in-visual-studio-for-mac"></a>Abrir scripts do Unity com o Visual Studio para Mac

Depois que o Visual Studio para Mac é [definido como o editor de script externo para Unity](setup-vsmac-tools-unity.md#configure-unity-for-use-with-visual-studio-for-mac), abrir qualquer script do editor do Unity iniciará ou trocará automaticamente para o Visual Studio para Mac com o script escolhido aberto.

Outra opção é abrir o Visual Studio para Mac sem nenhum script no editor de código-fonte selecionando **Abrir projeto C#** no menu **Ativos** no Unity.

![Abrir um projeto C#](media/using-vsmac-tools-unity-image1.png)

## <a name="unity-documentation-access"></a>Acesso de documentação do Unity

As Ferramentas do Visual Studio para Mac para Unity inclui um atalho para acessar a documentação da API do Unity. Para acessar a documentação da API do Unity no Visual Studio para Mac, posicione o cursor sobre a API do Unity você deseja conhecer e pressione o **comando ⌘ + ‘** .

## <a name="intellisense-for-unity-messages"></a>IntelliSense para mensagens do Unity
O mecanismo do Unity transmite mensagens para scripts monocomportamento, permitindo que os desenvolvedores escrevam código que reage a mensagens como OnMouseDown, OnTriggerEnter, etc. Como esses não são métodos virtuais na classe multicomportamento base, alguns IDEs, como o MonoDevelop, não têm funcionalidade de conclusão de código para mensagens do Unity.

No entanto, as Ferramentas do Visual Studio para Mac para Unity estende sua funcionalidade do IntelliSense para as mensagens do Unity. Isso torna mais fácil implementar mensagens Unity em scripts MonoBehaviour e auxilia no aprendizado da API do Unity. Para usar o IntelliSense para mensagens Unity:

1. Posicione o cursor em uma nova linha dentro do corpo de uma classe derivada de MonoBehaviour.

2. Comece a digitar o nome de uma mensagem do Unity, como `OnTriggerEnter`.

3. Depois que as letras “**ont**” forem digitadas, será exibida uma lista de sugestões do IntelliSense.

   ![Usando o IntelliSense](media/using-vsmac-tools-unity-image2.png)

4. A seleção na lista pode ser alterada de três maneiras:

   * Com as teclas de direção **Para cima** e **Para baixo**.

   * Clicando com o mouse no item desejado.

   * Continuando a digitar o nome do item desejado.

5. O IntelliSense pode inserir a mensagem Unity selecionada, incluindo todos os parâmetros necessários:

   * Pressionando **Tab**.

   * Pressionando **Enter**.

   * Clicando duas vezes no item selecionado.

   ![Inserir mensagem Unity do IntelliSense](media/using-vsmac-tools-unity-image3.png)

## <a name="adding-new-unity-files-and-folders"></a>Adicionar novos arquivos e pastas Unity

Embora sempre seja possível adicionar novos arquivos a um projeto do Unity no editor do Unity, o Visual Studio para Mac permite criar facilmente novos scripts, sombreadores, structs, enumerações e pastas do Unity no Visual Studio.

### <a name="add-a-new-c-monobehaviour-script"></a>Adicionar um novo script MonoBehaviour C#

Para adicionar um novo script MonoBehaviour C#, **clique com o botão direito do mouse na pasta Ativos** ou em um de seus subdiretórios no Painel de Soluções e selecione **Adicionar > Novo MonoBehaviour**.

![Adicionar novo MonoBehaviour](media/using-vsmac-tools-unity-image4.png)

### <a name="add-a-new-unity-shader"></a>Adicionar um novo sombreador do Unity

Para adicionar um novo sombreador do Unity, **clique com o botão direito do mouse na pasta Ativos** ou em um subdiretório no painel Solução e selecione **Adicionar > Novo Sombreador**.

### <a name="add-a-new-folder"></a>Adicionar uma nova pasta

Para adicionar uma nova pasta, **clique com o botão direito do mouse na pasta Ativos** ou em um subdiretório no Painel de Soluções e selecione **Adicionar > Nova Pasta**.

Essas adições são refletidas na janela Projeto do editor do Unity.

### <a name="to-rename-a-file-or-folder"></a>Renomear um arquivo ou pasta
**Clique com botão direito do mouse** no item a ser renomeado no Painel de Soluções e selecione **Renomear...** .

> [!NOTE]
> Se você tiver um novo projeto do Unity sem nenhum script e a pasta Ativos não for mostrada no Painel de Soluções no Visual Studio para Mac, adicione um script C# inicial de dentro do editor do Unity.

## <a name="unity-debugging"></a>Depuração do Unity

Projetos do Unity podem ser depurados com o Visual Studio para Mac.

### <a name="start-debugging"></a>Iniciar a depuração

Para iniciar a depuração:

1. Conecte-se ao Visual Studio para Unity clicando no botão **Executar** ou pressione **Comando + Enter** ou **F5**.

   ![Clique em Executar no Visual Studio](media/using-vsmac-tools-unity-image5.png)

2. Alterne para o Unity e clique no botão **Reproduzir** para executar o jogo no editor.

   ![Clique em Executar no Unity](media/using-vsmac-tools-unity-image6.png)

3. Quando o jogo estiver em execução no editor do Unity e ao mesmo conectado ao Visual Studio, qualquer ponto de interrupção encontrado pausará a execução do jogo e mostrará a linha de código em que o jogo atingiu o ponto de interrupção no Visual Studio para Mac.

### <a name="start-debugging-in-a-single-step"></a>Iniciar a depuração em uma única etapa

É possível iniciar a depuração e reproduzir o editor do Unity em uma única etapa diretamente do Visual Studio para Mac, escolhendo a configuração **Anexar ao Unity e Reproduzir**.

![Selecionar Anexar ao Unity e Reproduzir](media/using-vsmac-tools-unity-image8.png)

### <a name="stop-debugging"></a>Parar a depuração

Para interromper a depuração:

1. Clique no botão **Parar** no Visual Studio para Mac ou pressione **Shift + Comando + Enter**.

   ![Clique em Parar no Visual Studio](media/using-vsmac-tools-unity-image7.png)

> [!NOTE]
> Se você tiver iniciado a depuração usando a configuração **Anexar ao Unity e Reproduzir**, o botão **Parar** também interromperá o Unity.

Para saber mais sobre a depuração no Visual Studio para Mac, consulte [Usando o depurador](debugging.md).
