---
title: Conteúdo de pré-busca para aplicativos da Windows Store | Microsoft Docs
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
ms.openlocfilehash: 4ac6479b4dbb0815374174140deb0d660636ac9e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "74300527"
---
# <a name="prefetch-content-for-windows-store-apps"></a>Executar pré-busca de conteúdo para aplicativos da Windows Store
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Aplica-se somente ao Windows] (.. /Imagem/windows_only_content.png "windows_only_content")  
  
 Para tornar seu aplicativo da Windows Store mais responsivo, você pode solicitar que o Windows faça o pré-carregamento de algum conteúdo da Web, como páginas da Web ou imagens, no [cache wininet wininet do aplicativo](https://msdn.microsoft.com/0a06f2af-957a-4dff-a8cc-187370181b5c)[WinINet](https://msdn.microsoft.com/library/aa383630.aspx). Essa funcionalidade chama-se pré-busca. É especialmente eficiente para o conteúdo que é usado na inicialização, mas você também pode executar a pré-busca de outro conteúdo usado frequentemente. Os métodos da classe [Windows.Networking.BackgroundTransfer.ContentPrefetcher](https://msdn.microsoft.com/library/windows/apps/windows.networking.backgroundtransfer.contentprefetcher.aspx) permitem especificar os URIs do conteúdo que você deseja pré-carregar.  
  
 O Windows usa heurística para determinar quando e se a pré-busca deve ocorrer e quais recursos serão baixados. A heurística leva em conta condições de energia e rede do sistema da conta, o histórico de uso do aplicativo do usuário e os resultados das tentativas anteriores de pré-busca. No Visual Studio, você pode usar o comando **Disparar Pré-busca de Aplicativo da Windows Store** para forçar o Windows a ignorar a heurística ContentPrefetcher e pré-carregar todo o conteúdo da Web especificado. Isso pode ser útil se você quiser testar o comportamento ou desempenho do aplicativo com o conteúdo para pré-buscar em um estado conhecido (carregado ou não carregado).  
  
## <a name="to-force-preloading-of-contentprefetcher-specified-resources"></a>Para forçar o pré-carregamento dos recursos especificados do ContentPrefetcher  
 Este procedimento presume que você já definiu a funcionalidade ContentPrefetcher e especificou os URIs de conteúdo para pré-carregar em seu projeto de aplicativo. Para forçar o pré-carregamento de conteúdo quando os recursos especificados são novos ou modificados, você tem de iniciar e parar o aplicativo antes de escolher o comando **Disparar Pré-busca de Aplicativo da Windows Store**. Você executa o aplicativo primeiro para registrar os URIs. O comando **Disparar Pré-busca de Aplicativo da Windows Store** força o ContentPrefetcher a baixar o conteúdo e adicioná-lo ao cache. Nas execuções subsequentes do aplicativo, você pode presumir que o conteúdo esteja pré-carregado.  
  
1. Inicie o aplicativo para registrar os URIs de conteúdo para pré-busca com o aplicativo. No menu **Depurar**, escolha **Iniciar Depuração** (atalho do teclado: F5).  
  
2. **No menu Depurar**, escolha **Parar Depuração** (atalho do teclado: Shift+F5).  
  
3. No menu **Depurar**, escolha **Outros Destinos de Depuração** e escolha **Disparar Pré-busca de Aplicativo da Windows Store**.  
  
   Agora você pode depurar, testar ou analisar seu aplicativo com os recursos Web pré-buscados.  
  
> [!NOTE]
> Repita estas etapas sempre que adicionarem ou modificar o conteúdo da Web especificado.  
  
## <a name="see-also"></a>Consulte Também  
 [Postagem no blog: disparando a pré-busca para aplicativos da Windows Store no Visual Studio 2013 atualização 2](https://devblogs.microsoft.com/devops/triggering-prefetch-for-windows-store-apps-in-visual-studio-2013-update-2/)
