---
title: Realizar pré-busca de conteúdo para aplicativos da Windows Store | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
ms.assetid: b4481fef-3ebf-4f7d-9748-d43821a0ebac
caps.latest.revision: 14
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 04842202e8534c551212d7322ab74e9b0ace5848
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63446188"
---
# <a name="prefetch-content-for-windows-store-apps"></a>Executar pré-busca de conteúdo para aplicativos da Windows Store
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Aplica-se ao Windows apenas] (... /Image/windows_only_content.png "windows_only_content")  
  
 Para tornar seu aplicativo da Windows Store mais responsivo, você pode solicitar o Windows para pré-carregar algum conteúdo da web, como imagens, ou páginas da web para o aplicativo [WinINet](http://msdn.microsoft.com/0a06f2af-957a-4dff-a8cc-187370181b5c)[WinINet](http://msdn.microsoft.com/library/aa383630.aspx)cache. Essa funcionalidade chama-se pré-busca. É especialmente eficiente para o conteúdo que é usado na inicialização, mas você também pode executar a pré-busca de outro conteúdo usado frequentemente. Os métodos da classe [Windows.Networking.BackgroundTransfer.ContentPrefetcher](http://msdn.microsoft.com/library/windows/apps/windows.networking.backgroundtransfer.contentprefetcher.aspx) permitem especificar os URIs do conteúdo que você deseja pré-carregar. Confira a [Amostra de pré-busca de conteúdo](http://code.msdn.microsoft.com/windowsapps/ContentPrefetcher-Sample-432c8309) do SDK do Windows para obter exemplos de como adicionar a funcionalidade ContentPrefetcher ao seu aplicativo.  
  
 O Windows usa heurística para determinar quando e se a pré-busca deve ocorrer e quais recursos serão baixados. A heurística leva em conta condições de energia e rede do sistema da conta, o histórico de uso do aplicativo do usuário e os resultados das tentativas anteriores de pré-busca. No Visual Studio, você pode usar o comando **Disparar Pré-busca de Aplicativo da Windows Store** para forçar o Windows a ignorar a heurística ContentPrefetcher e pré-carregar todo o conteúdo da Web especificado. Isso pode ser útil se você quiser testar o comportamento ou desempenho do aplicativo com o conteúdo para pré-buscar em um estado conhecido (carregado ou não carregado).  
  
## <a name="to-force-preloading-of-contentprefetcher-specified-resources"></a>Para forçar o pré-carregamento dos recursos especificados do ContentPrefetcher  
 Este procedimento presume que você já definiu a funcionalidade ContentPrefetcher e especificou os URIs de conteúdo para pré-carregar em seu projeto de aplicativo. Para forçar o pré-carregamento de conteúdo quando os recursos especificados são novos ou modificados, você tem de iniciar e parar o aplicativo antes de escolher o comando **Disparar Pré-busca de Aplicativo da Windows Store**. Você executa o aplicativo primeiro para registrar os URIs. O comando **Disparar Pré-busca de Aplicativo da Windows Store** força o ContentPrefetcher a baixar o conteúdo e adicioná-lo ao cache. Nas execuções subsequentes do aplicativo, você pode presumir que o conteúdo esteja pré-carregado.  
  
1. Inicie o aplicativo para registrar os URIs de conteúdo para pré-busca com o aplicativo. No menu **Depurar**, escolha **Iniciar Depuração** (atalho do teclado: F5).  
  
2. Sobre o **Debug** menu, escolha **parar depuração** (atalho de teclado: SHIFT + F5).  
  
3. No menu **Depurar**, escolha **Outros Destinos de Depuração** e escolha **Disparar Pré-busca de Aplicativo da Windows Store**.  
  
   Agora você pode depurar, testar ou analisar seu aplicativo com os recursos Web pré-buscados.  
  
> [!NOTE]
> Repita estas etapas sempre que adicionarem ou modificar o conteúdo da Web especificado.  
  
## <a name="see-also"></a>Consulte também  
 [Postagem no blog: Acionar a pré-busca para aplicativos da Windows Store no Visual Studio 2013 atualização 2](http://blogs.msdn.com/b/visualstudioalm/archive/2014/02/06/triggering-prefetch-for-windows-store-apps-in-visual-studio-2013-update-2.aspx)
