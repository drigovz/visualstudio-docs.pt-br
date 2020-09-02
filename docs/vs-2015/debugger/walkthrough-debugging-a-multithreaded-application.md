---
title: 'Walkthrough: Depurando um aplicativo multithread | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- multithreaded debugging, walkthrough
- walkthroughs, multithreaded debugging
ms.assetid: 590ffd57-0556-43d8-8962-ee27e5b2b7d7
caps.latest.revision: 42
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 33ce391523a256bcb195deccf0c14868b5eae707
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65683091"
---
# <a name="walkthrough-debugging-a-multithreaded-application"></a>Instruções passo a passo: depurando um aplicativo multithread
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)] fornece uma janela de **threads** aprimorada e outros aprimoramentos da interface do usuário para facilitar a depuração de aplicativos multithread. Este passo a passo só levará alguns minutos e o ajudará a se familiarizar com os recursos da nova interface para depurar aplicativos de vários threads.  
  
 Para iniciar este passo a passo, você precisará de um projeto de aplicativo de vários threads. Siga as etapas listadas aqui para criar o projeto.  
  
#### <a name="to-create-the-walkthrough-project"></a>Para criar o projeto passo a passo  
  
1. No menu **arquivo** , escolha **novo** e, em seguida, clique em **projeto**.  
  
     A caixa de diálogo **Novo Projeto** aparecerá.  
  
2. Na caixa **tipo de projeto**s, clique no idioma de sua escolha: **Visual Basic**, **Visual C#** ou **Visual C++**.  
  
3. Na caixa **modelos** , escolha **aplicativo de console** ou **aplicativo de console CLR**.  
  
4. Na caixa **nome** , digite o nome MyThreadWalkthroughApp.  
  
5. Clique em **OK**.  
  
     Um novo projeto de console é exibido. Quando o projeto tiver sido criado, um arquivo de origem aparecerá. Dependendo da linguagem escolhida, o arquivo de origem poderá ser chamado Module1.vb, Program.cs ou MyThreadWalkthroughApp.cpp  
  
6. Exclua o código que aparece no arquivo de origem e substitua-o pelo código de exemplo que aparece na seção "criando um thread" do tópico [criando threads e passando dados na hora de início](https://msdn.microsoft.com/library/52b32222-e185-4f42-91a7-eaca65c0ab6d).  
  
7. No menu **Arquivo** , clique em **Salvar Tudo**.  
  
#### <a name="to-begin-the-walkthrough"></a>Para iniciar o passo a passo  
  
- Na janela de origem, procure o seguinte código:  
  
    ```vb  
    Thread.Sleep(3000)   
    Console.WriteLine(  
    ```  
  
```csharp  
Thread.Sleep(3000);  
Console.WriteLine();  
```  
  
```cpp  
Thread::Sleep(3000);  
Console.WriteLine();  
```  
  
#### <a name="to-start-debugging"></a>Para iniciar a depuração  
  
1. Clique com o botão direito do mouse na `Console.WriteLine` instrução, aponte para ponto de **interrupção** e clique em **Inserir ponto de interrupção**.  
  
     Na medianiz no lado esquerdo da janela de origem, uma bola vermelha aparece. Isso indica que um ponto de interrupção agora está definido nesse local.  
  
2. No menu **Depurar** , clique em **Iniciar Depuração**.  
  
     A depuração é iniciada, seu aplicativo de console começa a ser executado e, em seguida, para no ponto de interrupção.  
  
3. Se a janela do aplicativo de console tiver o foco neste momento, clique na janela do [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] para retornar o foco para o [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].  
  
4. Na janela de origem, localize a linha que contém o seguinte código:  
  
    ```vb  
    Thread.Sleep(5000)   
    ```  
  
```csharp  
Thread.Sleep(3000);  
```  
  
```cpp  
Thread::Sleep(3000);  
```  
  
1. 
  
#### <a name="to-discover-the-thread-marker"></a>Para descobrir o marcador de thread  
  
1. Clique com o botão direito do mouse na janela **threads** e clique em **Mostrar threads na origem**.  
  
2. Examine a medianiz no lado esquerdo da janela. Nessa linha, você verá um ícone semelhante a dois threads de pano. Um thread é vermelho e o outro é azul. O marcador de thread indica que um thread está parado nesse local. Possivelmente, o thread está parado nesse local.  
  
3. Passe o ponteiro sobre o marcador de thread. Um DataTip que aparece. O DataTip mostra o nome e o número de ID do thread para cada thread parado. Nesse caso, há apenas um thread, cujo nome é provavelmente `<noname>`.  
  
4. Clique com o botão direito no marcador de thread. Observe as opções no menu de atalho.  
  
   Este ícone é um *marcador de thread*:  
  
   ![Marcador de thread](../debugger/media/threadmarker.gif "ThreadMarker")  
  
## <a name="flagging-and-unflagging-threads"></a>Sinalizando e removendo a sinalização de threads  
 No [!INCLUDE[vs_orcas_long](../includes/vs-orcas-long-md.md)], você pode sinalizar os threads para os quais deseja dar atenção especial. Sinalizar threads é uma boa maneira de manter o controle de threads importantes e ignorar threads com os quais você não precisa se preocupar.  
  
#### <a name="to-flag-threads"></a>Para sinalizar threads  
  
1. No menu **Exibir** , aponte para **barras de ferramentas**.  
  
     Verifique se a barra de ferramentas **local de depuração** está selecionada.  
  
2. Vá para a barra de ferramentas **local de depuração** e clique na lista **thread** .  
  
    > [!NOTE]
    > Você pode reconhecer essa barra de ferramentas por três listas proeminentes: **processo**, **thread**e **pilha de pilhas**.  
  
3. Observe quantos threads aparecem na lista.  
  
4. Volte para a janela de origem e clique com o botão direito do mouse no marcador de **thread** novamente.  
  
5. No menu de atalho, aponte para **sinalizador**e clique no nome do thread e no número da ID.  
  
6. Volte para a barra de ferramentas **local de depuração** e clique na lista **thread** novamente.  
  
     Somente o thread sinalizado agora aparece na lista. O botão de sinalizador que está logo à direita da lista de **threads** . O ícone de sinalizador no botão estava esmaecido antes. Agora, é um vermelho contínuo e brilhante.  
  
7. Passe o ponteiro sobre o ícone do sinalizador.  
  
     Um pop-up será exibido. Essa janela pop-up informa em qual modo a lista de **threads** está: **Mostrar somente threads sinalizados**.  
  
8. Clique no botão sinalizador para alternar novamente para o modo **Mostrar todos os threads** .  
  
9. Clique na lista de **threads** novamente e verifique se agora você pode ver todos os threads novamente.  
  
10. Clique no botão sinalizador para alternar novamente para **Mostrar somente threads sinalizados**.  
  
11. No menu **Depurar**, aponte para **Janelas** e, em seguida, clique em **Threads**.  
  
     A janela **threads** é exibida. Um thread tem um ícone de sinalizador destacado anexado.  
  
12. Na janela de origem, clique com o botão direito no marcador de thread novamente.  
  
     Observe quais opções estão disponíveis no menu de atalho. Em vez de **sinalizador**, agora você verá **remover sinalizador**. Não clique em **desmarcar**.  
  
13. Vá para o próximo procedimento sobre como remover a sinalização do thread.  
  
#### <a name="to-unflag-threads"></a>Para remover a sinalização de threads  
  
1. Na janela **threads** , clique com o botão direito do mouse na linha correspondente ao thread sinalizado.  
  
     Um menu de atalho é exibido. Ele tem opções para **remover o sinalizador** e **desmarcar tudo**.  
  
2. Para remover o sinalizador do thread, clique em **desmarcar**.  
  
3. Clique no ícone de sinalizador vermelho.  
  
4. Examine a barra de ferramentas **local de depuração** novamente. O sinalizador do botão ficará esmaecido novamente. Você removerá a sinalização do único thread sinalizado. Como não há threads sinalizados, a barra de ferramentas resumiu para **Mostrar todos os modos de threads** . Clique na lista **thread** e verifique se você pode ver todos os threads.  
  
5. Volte para a janela **threads** e examine as colunas Information.  
  
     Na parte superior de cada coluna, a maioria dos botões têm títulos que identificam a coluna. No entanto, a primeira coluna à esquerda não tem título. Em vez disso, tem um ícone, que é o contorno de um sinalizador. Você observará o mesmo contorno em cada linha da lista de thread. O contorno significa que a sinalização foi removida do thread.  
  
6. Clique nos contornos do sinalizador para dois threads, o segundo e o terceiro da parte inferior da lista.  
  
     Os ícones de sinalizador ficam vermelho contínuo, em vez de contornos vazado.  
  
7. Clique no botão na parte superior da coluna do sinalizador.  
  
     A ordem da lista de thread foi alterada quando você clicou no botão. A lista de thread agora é classificada com os threads sinalizados na parte superior.  
  
8. Novamente, clique no botão na parte superior da coluna do sinalizador.  
  
     A ordem de classificação foi modificada novamente.  
  
## <a name="more-about-the-threads-window"></a>Mais sobre a janela de threads  
  
#### <a name="to-learn-more-about-the-threads-window"></a>Para saber mais sobre a janela de threads  
  
1. Na janela **threads** , examine a terceira coluna à esquerda. O botão na parte superior desta coluna diz **ID**.  
  
2. Clique em **ID**.  
  
     A lista de thread agora é classificada pelo número de identificação do thread.  
  
3. Clique com o botão direito em qualquer thread na lista. No menu de atalho, clique em **exibição hexadecimal**.  
  
     O formato dos números da ID de thread é alterado.  
  
4. Passe o ponteiro de mouse sobre qualquer thread na lista.  
  
     Depois de um atraso momentâneo, um DataTip é exibido. Ele mostra uma pilha de chamadas parcial para o thread.  
  
5. Examine a quarta coluna à esquerda, que é rotulada como **categoria**. Os threads são classificados em categorias.  
  
     O primeiro thread criado em um processo é chamado de thread principal. Localize-o na lista de thread.  
  
6. Clique com o botão direito do mouse no thread principal e clique em **alternar para thread**.  
  
     Uma caixa de diálogo de aviso é exibida. Ela indica que o [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] não pode exibir o código-fonte do thread principal.  
  
     Clique em **OK**.  
  
7. Examine a janela **pilha de chamadas** e a barra de ferramentas do **local de depuração** .  
  
     O conteúdo da janela **pilha de chamadas** foi alterado.  
  
## <a name="switching-the-active-thread"></a>Alternando o thread ativo  
  
#### <a name="to-switch-threads"></a>Para alternar segmentos  
  
1. Na janela **threads** , examine a segunda coluna da esquerda. O botão na parte superior dessa coluna não tem texto ou ícone. Esta coluna é a coluna **thread ativa** .  
  
2. Examine a coluna **thread ativo** e observe que um thread tem uma seta amarela. Este é o *indicador de thread ativo*.  
  
3. Anote o número de ID do thread onde o indicador de thread ativo está localizado. Você moverá o indicador de thread ativo para outro thread, mas terá que colocá-lo de volta onde terminou.  
  
4. Clique com o botão direito do mouse em outro thread e clique em **alternar para thread**.  
  
5. Examine a janela **pilha de chamadas** na janela de origem. O conteúdo foi alterado.  
  
6. Examine a barra de ferramentas do **local de depuração** . O thread ativo foi alterado lá também.  
  
7. Vá para a barra de ferramentas do **local de depuração** . Clique na caixa **thread** e escolha um thread diferente na lista suspensa.  
  
8. Examine a janela **threads** . O indicador de thread ativo foi alterado.  
  
9. Na janela de origem, clique com o botão direito em u marcador de thread. No menu de atalho, aponte para **alternar para** e clique em um nome de thread/número de ID.  
  
     Agora você viu três maneiras de alterar o thread ativo: usando a janela **threads** , a caixa **thread** na barra de ferramentas **local de depuração** e o indicador de thread na janela de origem.  
  
     Com o indicador de thread, você pode alternar somente para threads que pararam nesse local específico. Ao usar a janela **Threads** e a barra de ferramentas **Localização de Depuração**, você pode alternar para qualquer thread.  
  
## <a name="freezing-and-thawing-thread-execution"></a>Congelando e descongelando a execução de thread  
  
#### <a name="to-freeze-and-unfreeze-threads"></a>Para congelar e descongelar threads  
  
1. Na janela **threads** , clique com o botão direito do mouse em qualquer thread e clique em **congelar**.  
  
2. Examine a coluna de thread ativo. O par de barras verticais agora aparece ali. Essas duas barras azuis indicam que o thread está congelado.  
  
3. Examine a coluna **suspender** . A contagem de suspensão para o thread agora é 1.  
  
4. Clique com o botão direito do mouse no thread congelado e clique em **descongelar**.  
  
     A coluna de thread ativa e a coluna de **suspensão** mudam.  
  
## <a name="see-also"></a>Consulte Também  
 [Depurar aplicativos multissegmentados](../debugger/debug-multithreaded-applications-in-visual-studio.md)   
 [Como alternar para outro thread durante a depuração](../debugger/how-to-switch-to-another-thread-while-debugging.md)
