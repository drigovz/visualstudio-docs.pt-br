---
title: Criar visualizadores personalizados de dados | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.visualizer.troubleshoot
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
- debugger, visualizers
- visualizers
ms.assetid: c24c006f-f2ac-429f-89db-677fc0c6e1ea
caps.latest.revision: 31
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: f890277190b9b4d28873e1fe394abdcd95b8a3a6
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "58922962"
---
# <a name="create-custom-visualizers-of-data"></a>Criar visualizadores personalizados de dados
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Os visualizadores são componentes do [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] interface de usuário do depurador. Um *visualizer* cria uma caixa de diálogo ou outra interface para exibir uma variável ou objeto de forma que seja apropriada para seu tipo de dados. Por exemplo, um visualizador de HTML interpreta uma cadeia de caracteres de HTML e exibe o resultado como seria exibido em uma janela do navegador; um visualizador de bitmap interpreta uma estrutura de bitmap e exibe o gráfico que o representa. Alguns visualizadores permitem modificar assim como exibir os dados.  
  
 O depurador do [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] inclui seis visualizadores padrão. Esses são o texto, os visualizadores HTML, XML e JSON, todos funcionam em objetos de cadeia de caracteres; o Visualizador de árvore do WPF, para exibir as propriedades de uma árvore visual do objeto WPF; e o Visualizador de conjunto de dados, o que funciona para objetos de DataSet, DataView e DataTable. Visualizadores adicionais podem estar disponíveis para download da Microsoft Corporation no futuro e estão disponíveis por meio de terceiros e da comunidade. Além disso, você pode escrever seus próprios visualizadores e instalá-los no [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] depurador.  
  
> [!NOTE]
>  Na **Store** aplicativos, somente o texto padrão, os visualizadores HTML, XML e JSON são suportados. Não há suporte para visualizadores personalizados (criados pelo usuário).  
  
 Os visualizadores são representados no depurador por um ícone de lupa. Quando você vir o ícone de lupa em uma **DataTip**, em uma janela de variáveis do depurador ou na **QuickWatch** caixa de diálogo, você pode clicar na lupa para selecionar um visualizador apropriado para o tipo de dados o objeto correspondente.  
  
 Os visualizadores não têm suporte na Compact Framework.  
  
> [!NOTE]
>  Os visualizadores do depurador exigem privilégios maiores do que são permitidos por um aplicativo de confiança parcial. Como resultado disso, os visualizadores não serão carregados quando você for interrompido no código com confiança parcial. Para depurar usando um visualizador, você deverá executar o código com confiança total.  
  
## <a name="in-this-section"></a>Nesta seção  
 [Como: Escrever um visualizador](../debugger/how-to-write-a-visualizer.md)  
  
 [Passo a passo: Como escrever um visualizador em C#](../debugger/walkthrough-writing-a-visualizer-in-csharp.md)  
  
 [Como: Instalar um visualizador](../debugger/how-to-install-a-visualizer.md)  
  
 [Como: Testar e depurar um visualizador](../debugger/how-to-test-and-debug-a-visualizer.md)  
  
 [Referência de API do visualizador](../debugger/visualizer-api-reference.md)  
  
## <a name="related-sections"></a>Seções relacionadas  
 [Exibindo dados no depurador](../debugger/viewing-data-in-the-debugger.md)
