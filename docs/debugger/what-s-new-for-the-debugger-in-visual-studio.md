---
title: O que há de novo para o depurador no Visual Studio 2017 | Microsoft Docs
titleSuffix: ''
ms.date: 01/22/2018
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugger, what's new
- what's new [debugger]
- debugging [Visual Studio], what's new
- what's new [Visual Studio], debugging
ms.assetid: 2aed9caa-2384-4e49-8595-82d8b06cf271
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
monikerRange: vs-2017
ms.openlocfilehash: 130387fedce065948ebe09ea605e32cf89ad820b
ms.sourcegitcommit: ea182703e922c74725045afc251bcebac305068a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2019
ms.locfileid: "71210597"
---
# <a name="whats-new-for-the-debugger-in-visual-studio-2017"></a>Novidades do depurador no Visual Studio 2017

O depurador inclui estes novos recursos:

- Novidade na versão 15,5, o **depurador de instantâneos** tira um instantâneo dos aplicativos em produção quando o código que você está interessado em executar. Para instruir o depurador a tirar um instantâneo, defina snappoints e logpoints em seu código. O depurador permite ver exatamente o que deu errado sem afetar o tráfego do seu aplicativo de produção. O Depurador de Instantâneo pode ajudar a reduzir drasticamente o tempo que leva para resolver problemas que ocorrem em ambientes de produção.

    A coleção de instantâneos está disponível para os seguintes aplicativos Web em execução no Serviço de Aplicativo do Azure:

  * Aplicativos ASP.NET em execução no .NET Framework 4.6.1 ou posterior.
  * Aplicativos ASP.NET Core em execução no .NET Core 2.0 ou posterior no Windows.

    Para obter mais informações, confira [Depurar aplicativos ASP.NET dinâmicos usando o Depurador de Instantâneos](../debugger/debug-live-azure-applications.md).

- Novidade na versão 15,5 somente no Visual Studio Enterprise, o **IntelliTrace faz** um instantâneo automaticamente do seu aplicativo em cada ponto de interrupção e evento de etapa do depurador. Os instantâneos registrados permitem retornar aos pontos de interrupção ou às etapas anteriores e exibir o estado do aplicativo como ele era no passado. O retrocesso do IntelliTrace poderá poupar seu tempo quando você desejar ver o estado do aplicativo anterior, mas não desejar reiniciar a depuração nem recriar o estado do aplicativo desejado.

    É possível navegar e exibir instantâneos usando os botões **Voltar** e **Avançar** na barra de ferramentas Depurar. Esses botões navegam pelos eventos exibidos na guia **Eventos** na janela **Ferramentas de Diagnóstico**.

    ![Botões Voltar e Avançar Etapa](../debugger/media/intellitrace-step-back-icons-description.png  "Botões Voltar e Avançar Etapa")

    Para obter mais informações, confira a página [Inspecionar estados anteriores do aplicativo usando o IntelliTrace](../debugger/view-historical-application-state.md).

- O **auxiliar de exceção** substitui o assistente de exceção e aparece em uma caixa de diálogo não modal onde ocorreu o erro. O **auxiliar de exceção** fornece acesso mais rápido a quaisquer exceções internas, análise adicional pelo depurador (se disponível) e acesso imediato às configurações de **exceção** para a exceção. O auxiliar de exceção também pode ser arrastado para uma exibição flutuante se estiver bloqueando algo que você precisa ver.

    Por exemplo, uma **NullReferenceException** agora mostra a variável que tem a referência nula (informações extras).

    ![Auxiliar de exceção do depurador](../debugger/media/dbg-exception-helper.png "DbgExceptionHelper")

    Para obter mais informações, consulte a postagem de blog [Usando o novo Auxiliar de Exceção no Visual Studio](https://blogs.msdn.microsoft.com/visualstudioalm/2016/03/31/using-the-new-exception-helper-in-visual-studio-15-preview/).

- Agora você pode executar em uma linha de código enquanto estiver em pausa no depurador, selecionando o ícone de seta **executar execução para aqui** verde (você vê o ícone ao passar o mouse sobre uma linha de código). Isso elimina a necessidade de definir pontos de interrupção temporários.

    ![Execução do depurador para clicar](../debugger/media/dbg-run-to-click.png "DbgRunToClick")

- Você pode definir condições em exceções na caixa de diálogo **configurações de exceção** (você pode fazer isso usando o ícone **Editar condição** na caixa de diálogo Configurações de exceção ou usando o menu de clique com o botão direito do mouse na exceção.) Atualmente, as condições com suporte incluem os nomes de módulo a serem incluídos ou excluídos para a exceção.

    ![Condições em uma exceção](../debugger/media/dbg-conditional-exception.png "DbgConditionalException")

- A caixa de diálogo anexar ao processo inclui um novo recurso de pesquisa que pode ajudá-lo a identificar mais rapidamente o processo ao qual você precisa se anexar.

    ![Pesquisar em anexo ao processo](../debugger/media/dbg-attach-to-process-search.png "DbgAttachToProcessSearch")

Para obter mais informações sobre esses novos recursos, consulte as [notas de [!include[vs_dev15](../misc/includes/vs_dev15_md.md)]versão do ](/visualstudio/releasenotes/vs2017-relnotes).

## <a name="see-also"></a>Consulte também

- [Depurando no Visual Studio](../debugger/index.yml)
- [Introdução ao depurador](../debugger/debugger-feature-tour.md)