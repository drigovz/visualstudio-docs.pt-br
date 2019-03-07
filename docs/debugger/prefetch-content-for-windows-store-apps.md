---
title: Depurar usando o conteúdo de pré-busca em aplicativos UWP | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- uwp
ms.openlocfilehash: 7e59548ac46196f86813aa312e68bbe043edf701
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MTE95
ms.contentlocale: pt-BR
ms.lasthandoff: 02/22/2019
ms.locfileid: "56701271"
---
# <a name="debug-uwp-apps-using-prefetched-content-in-visual-studio"></a>Depurar aplicativos UWP usando a pré-busca de conteúdo no Visual Studio

 Para tornar seu aplicativo da UWP mais responsivo, você pode solicitar o Windows para pré-carregar algum conteúdo da web, como imagens, ou páginas da web para o aplicativo [WinINet](/windows/desktop/WinInet/about-wininet) cache. Essa funcionalidade chama-se pré-busca. É especialmente eficiente para o conteúdo usado na inicialização, mas você também pode executar a pré-busca de outro conteúdo usado frequentemente. Os métodos da classe [Windows.Networking.BackgroundTransfer.ContentPrefetcher](/uwp/api/Windows.Networking.BackgroundTransfer.ContentPrefetcher) permitem especificar os URIs do conteúdo que você deseja pré-carregar. Confira a [Amostra de pré-busca de conteúdo](https://code.msdn.microsoft.com/windowsapps/ContentPrefetcher-Sample-432c8309) do SDK do Windows para obter exemplos de como adicionar a funcionalidade ContentPrefetcher ao seu aplicativo.

 O Windows usa heurística para determinar quando e se a pré-busca deve ocorrer e quais recursos serão baixados. A heurística leva em conta condições de energia e rede do sistema da conta, o histórico de uso do aplicativo do usuário e os resultados das tentativas anteriores de pré-busca. No Visual Studio, você pode usar o comando **Disparar Pré-busca de Aplicativo da Windows Store** para forçar o Windows a ignorar a heurística ContentPrefetcher e pré-carregar todo o conteúdo da Web especificado. Isso pode ser útil se você quiser testar o comportamento ou desempenho do aplicativo com o conteúdo para pré-buscar em um estado conhecido (carregado ou não carregado).

## <a name="to-force-preloading-of-contentprefetcher-specified-resources"></a>Para forçar o pré-carregamento dos recursos especificados do ContentPrefetcher
 Este procedimento presume que você já definiu a funcionalidade ContentPrefetcher e especificou os URIs de conteúdo para pré-carregar em seu projeto de aplicativo. Para forçar o pré-carregamento de conteúdo quando os recursos especificados são novos ou modificados, você tem de iniciar e parar o aplicativo antes de escolher o comando **Disparar Pré-busca de Aplicativo da Windows Store**. Você executa o aplicativo primeiro para registrar os URIs. O comando **Disparar Pré-busca de Aplicativo da Windows Store** força o ContentPrefetcher a baixar o conteúdo e adicioná-lo ao cache. Nas execuções subsequentes do aplicativo, você pode presumir que o conteúdo esteja pré-carregado.

1. Inicie o aplicativo para registrar os URIs de conteúdo para pré-busca com o aplicativo. No menu **Depurar**, escolha **Iniciar Depuração** (atalho do teclado: F5).

2. **No menu Depurar**, escolha **Parar Depuração** (atalho do teclado: Shift+F5).

3. No menu **Depurar**, escolha **Outros Destinos de Depuração** e escolha **Disparar Pré-busca de Aplicativo da Windows Store**.

   Agora você pode depurar, testar ou analisar seu aplicativo com os recursos Web pré-buscados.

> [!NOTE]
>  Repita estas etapas sempre que adicionarem ou modificar o conteúdo da Web especificado.

## <a name="see-also"></a>Consulte também
- [Postagem de blog: acionar a pré-busca para aplicativos Windows da Store no Visual Studio 2013 atualização 2](https://devblogs.microsoft.com/devops/triggering-prefetch-for-windows-store-apps-in-visual-studio-2013-update-2/)