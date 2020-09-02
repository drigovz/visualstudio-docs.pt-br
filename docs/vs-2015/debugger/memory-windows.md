---
title: Janelas de memória | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.memory
dev_langs:
- FSharp
- VB
- CSharp
- C++
- JScript
- VB
- CSharp
- C++
helpviewer_keywords:
- Memory window
- strings [Visual Studio], viewing
- debugger [Visual Studio], Memory window
- memory [Visual Studio], debugging
- debugging [Visual Studio], Memory window
- buffers, viewing
ms.assetid: 7f7a0439-10e4-4966-bb2d-51f04cda4fe2
caps.latest.revision: 37
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: e60f9b3c9acf1377139fee27486bb10251d8804a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68158464"
---
# <a name="memory-windows"></a>Janelas de memória
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

A janela **memória** fornece uma exibição do espaço de memória usado pelo seu aplicativo. A janela **inspeção** , caixa de diálogo **QuickWatch** , janela **autos** e janela **locais** mostram o conteúdo das variáveis, que são armazenadas em locais específicos na memória. Mas a janela **memória** mostra a imagem em larga escala. Esta exibição pode ser conveniente para examinar grandes partes de dados (buffers ou grandes cadeias de caracteres, por exemplo) que não são exibidas corretamente nas outras janelas. No entanto, a janela de **memória** não está limitada à exibição de dados. Ela exibirá tudo no espaço de memória, não importa se o conteúdo for dados, código ou bits aleatórios de lixo na memória não atribuída.  
  
 A janela **memória** estará disponível somente se a depuração no nível de endereço estiver habilitada na caixa de diálogo **Opções** , nó de**depuração** . A janela **memória** não está disponível para script ou SQL, que são linguagens que não reconhecem o conceito de memória.  
  
## <a name="opening-a-memory-window"></a>Abrindo uma janela de memória  
  
#### <a name="to-open-a-memory-window"></a>Para abrir uma janela de memória  
  
1. Inicie a depuração, se você já não estiver no modo de depuração.  
  
2. No menu **depurar** , aponte para **Windows**. Em seguida, aponte para **memória** e clique **em memória 1**, **memória 2**, **memória 3**ou **memória 4**. (Edições de nível inferior do [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] têm apenas uma janela de **memória** . Se você estiver usando uma dessas edições, basta clicar em **memória**.)  
  
## <a name="paging-in-the-memory-window"></a>Paginação na janela de memória  
 A janela **memória** tem uma barra de rolagem vertical que opera de maneira não padrão. O espaço de endereço de um computador moderno é muito grande e você pode preferir arrastar a caixa de rolagem para um local aleatório. Por esse motivo, a caixa de rolagem é carregada e sempre permanece no centro da barra de rolagem. Em aplicativos de código nativo, você pode rolar a página para cima ou para baixo, mas não pode rolar livremente.  
  
 Um endereço de memória mais alto aparece na parte inferior da janela. Para exibir um endereço mais alto, role para baixo, não para cima.  
  
#### <a name="to-page-up-or-down-in-memory"></a>Para mover para cima ou para baixo na memória  
  
1. Para rolar a página para baixo (mover para um endereço de memória mais alto), clique abaixo da caixa de rolagem na barra de rolagem vertical.  
  
2. Para rolar a página para cima (mover para um endereço de memória mais baixo), clique acima da caixa de rolagem na barra de rolagem vertical.  
  
## <a name="selecting-a-memory-location"></a>Selecionando um local de memória  
 Se você quiser se mover instantaneamente para um local selecionado na memória, poderá fazer isso usando uma operação de arrastar e soltar ou editando o valor na caixa **endereço** . A caixa de **endereço** aceita não apenas valores numéricos, mas também expressões que são avaliadas como endereços. Por padrão, a janela **memória** trata uma expressão de **endereço** como uma expressão dinâmica, que é reavaliada à medida que seu programa é executado. As expressões dinâmicas podem ser muito úteis. Por exemplo, você pode usá-las para exibir a memória que é tocada por um ponteiro.  
  
#### <a name="to-select-a-memory-location-by-dragging-and-dropping"></a>Para selecionar um local de memória arrastando e soltando  
  
1. Em qualquer janela, selecione um endereço de memória ou variável de ponteiro que contém um endereço de memória.  
  
2. Arraste o endereço ou o ponteiro para a janela **memória** .  
  
#### <a name="to-select-a-memory-location-by-editing"></a>Para selecionar um local de memória editando  
  
1. Na janela **memória** , selecione a caixa **endereço** .  
  
2. Digite ou cole o endereço que você deseja ver e pressione **Enter**.  
  
## <a name="changing-the-way-the-memory-window-displays-information"></a>Alterando o modo como a janela de memória exibe informações  
 Você pode personalizar a maneira como a janela **Memória** mostra o conteúdo da memória. Por padrão, o conteúdo da memória aparece como inteiros de um byte em formato hexadecimal e o número de colunas é determinado automaticamente pela largura atual da janela.  
  
#### <a name="to-change-the-format-of-the-memory-contents"></a>Para alterar o formato do conteúdo de memória  
  
1. Clique com o botão direito do mouse na janela **memória** .  
  
2. Escolha o formato que você deseja.  
  
#### <a name="to-change-the-number-of-columns-in-the-memory-window"></a>Para alterar o número de colunas na janela de memória  
  
1. Na barra de ferramentas na parte superior da janela **memória** , localize a lista **colunas** .  
  
2. Na lista **colunas** , selecione o número de colunas que você deseja exibir ou selecione **automático** para ajuste automático para se ajustar à largura da janela.  
  
   Se você não quiser que o conteúdo da janela de **memória** mude à medida que seu programa for executado, você poderá desativar a avaliação de expressão dinâmica.  
  
#### <a name="to-toggle-live-evaluation"></a>Para ativar/desativar a avaliação dinâmica  
  
1. Clique com o botão direito do mouse na janela **memória** .  
  
2. No menu de atalho, clique em **reavaliar automaticamente**.  
  
    Se a avaliação dinâmica estiver ativa, a opção será selecionada e clicar nela a desativará. Se a avaliação dinâmica estiver inativa, a opção não será selecionada e clicar nela a ativará.  
  
   Você pode ocultar ou exibir a barra de ferramentas na parte superior da janela **Memória**. Você não terá acesso à caixa de endereço ou outras ferramentas enquanto a barra de ferramentas estiver oculta.  
  
#### <a name="to-toggle-the-toolbar"></a>Para ativar/desativar a barra de ferramentas  
  
1. Clique com o botão direito do mouse em uma janela de **memória** .  
  
2. No menu de atalho, clique em **Mostrar barra de ferramentas**.  
  
     A barra de ferramentas é exibida ou desaparece, dependendo do seu estado anterior.  
  
## <a name="following-a-pointer-through-memory"></a>Seguindo um ponteiro pela memória  
 Em aplicativos de código nativo, você poderá usar nomes de registro como expressões dinâmicas. Por exemplo, você pode usar o ponteiro de pilhas para seguir a pilha.  
  
#### <a name="to-follow-a-pointer-through-memory"></a>Para seguir um ponteiro pela memória  
  
1. Na caixa **endereço** da janela de **memória** , digite uma expressão de ponteiro. A variável de ponteiro deve estar no escopo atual. Dependendo da linguagem, você poderá ter que remover a referência a ele.  
  
2. Pressione **ENTER**.  
  
     Agora, quando você usar um comando de execução como **etapa**, o endereço de memória exibido será alterado automaticamente conforme o ponteiro for alterado.  
  
## <a name="see-also"></a>Consulte Também  
 [Exibindo dados no depurador](../debugger/viewing-data-in-the-debugger.md)
