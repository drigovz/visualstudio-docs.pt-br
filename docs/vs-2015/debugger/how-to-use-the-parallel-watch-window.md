---
title: 'Como: Use a janela Inspeção paralela | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.parallelwatch
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- debugger, parallel watch window
ms.assetid: 28004d9b-420c-48f7-b80e-ab1519802558
caps.latest.revision: 19
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: b588168b62a9219d0de703a5deb6dbe153df6305
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63445095"
---
# <a name="how-to-use-the-parallel-watch-window"></a>Como: Use a janela Inspeção paralela
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Na janela Inspeção Paralela, você pode exibir simultaneamente os valores que uma expressão mantém em vários threads. Cada linha representa um thread que está sendo executado em um aplicativo, mas um thread pode ser representado em várias linhas. Mais especificamente, cada linha representa uma chamada de função cuja assinatura de função corresponde à função no registro de ativação atual. Você pode classificar, reorganizar, remover e agrupar os itens que estão nas colunas. Você pode sinalizar, remover sinalização, congelar (suspender) e descongelar (retomar) threads. As colunas a seguir são exibidas na janela **Inspeção Paralela**:  
  
- A coluna do sinalizador, na qual você pode marcar um thread ao qual deseja prestar atenção especial.  
  
- A coluna do quadro, na qual uma seta indica o quadro selecionado.  
  
- Uma coluna configurável que pode exibir o computador, o processo, o bloco, a tarefa e o thread.  
  
  > [!TIP]
  > Você deve abrir o **tarefa paralela** janela para exibir as informações da tarefa na **inspeção paralela** janela.  
  
- O  **\<Adicionar inspeção >** coluna, na qual você pode inserir expressões para assistir.  
  
  [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]  
  
### <a name="to-display-the-parallel-watch-window"></a>Para exibir a janela Inspeção Paralela  
  
1. Defina um ponto de interrupção no código.  
  
2. Na barra de menus, escolha **Depurar**, **Iniciar Depuração**. Aguarde até que o aplicativo atinja o ponto de interrupção.  
  
3. Na barra de menus, escolha **Depurar**, **Janelas**, **Inspeção Paralela** e selecione uma janela de inspeção. Você pode abrir até quatro janelas.  
  
### <a name="to-add-a-watch-expression"></a>Para adicionar uma expressão de inspeção  
  
- Selecione  **\<Adicionar inspeção >** e, em seguida, especifique uma expressão de inspeção.  
  
### <a name="to-flag-or-unflag-a-thread"></a>Para sinalizar ou remover sinalização de um thread  
  
- Selecione a coluna do sinalizador para a linha, ou abra o menu de atalho para o thread e escolha **sinalizador** ou **Remover sinalização**.  
  
### <a name="to-display-only-flagged-threads"></a>Para exibir somente threads sinalizados  
  
- Escolha o botão Mostrar apenas sinalizados no canto superior esquerdo dos **inspeção paralela** janela.  
  
### <a name="to-switch-frames"></a>Para alternar quadros  
  
- Clique duas vezes na coluna do quadro. (Teclado: Selecione a linha e pressione Enter.)  
  
### <a name="to-sort-a-column"></a>Para classificar uma coluna  
  
- Selecione o título da coluna.  
  
### <a name="to-group-threads"></a>Para agrupar threads  
  
- Abra o menu de atalho da janela Inspeção Paralela, escolha **Agrupar por** e selecione o item de submenu apropriado.  
  
### <a name="to-freeze-or-thaw-threads"></a>Para congelar ou descongelar threads  
  
- Abra o menu de atalho da linha e escolha **Congelar** ou **Descongelar**.  
  
### <a name="to-export-the-data-in-the-parallel-watch-window"></a>Para exportar os dados na janela Inspeção Paralela  
  
- Escolha o botão **Abrir no Excel** e, depois, **Abrir no Excel** ou **Exportar para CSV**.  
  
### <a name="to-filter-by-a-boolean-expression"></a>Para filtrar por uma expressão booliana  
  
- Insira uma expressão booliana na caixa **Filtrar por Expressão Booliana**. O depurador avalia a expressão para cada contexto de thread. Apenas as linhas nas quais o valor é `true` é exibido.  
  
## <a name="see-also"></a>Consulte também  
 [Depurar aplicativos multi-threaded](../debugger/debug-multithreaded-applications-in-visual-studio.md)   
 [Como: Usar a janela Threads de GPU](../debugger/how-to-use-the-gpu-threads-window.md)   
 [Passo a passo: depurar um aplicativo C++ AMP](http://msdn.microsoft.com/library/40e92ecc-f6ba-411c-960c-b3047b854fb5)
