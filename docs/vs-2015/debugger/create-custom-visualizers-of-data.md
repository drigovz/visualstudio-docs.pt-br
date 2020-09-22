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
ms.openlocfilehash: 50df868f0e01d49d4c49bccae32d743d5291a066
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "90838613"
---
# <a name="create-custom-visualizers-of-data"></a>Criar visualizadores personalizados de dados
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Os visualizadores são componentes da [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] interface do usuário do depurador. Um *Visualizador* cria uma caixa de diálogo ou outra interface para exibir uma variável ou objeto de uma maneira apropriada ao seu tipo de dados. Por exemplo, um visualizador de HTML interpreta uma cadeia de caracteres de HTML e exibe o resultado como seria exibido em uma janela do navegador; um visualizador de bitmap interpreta uma estrutura de bitmap e exibe o gráfico que o representa. Alguns visualizadores permitem modificar assim como exibir os dados.  
  
 O depurador do [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] inclui seis visualizadores padrão. Estes são os visualizadores de texto, HTML, XML, e JSON e todos funcionam em objetos de cadeia de caracteres; o visualizador de árvore do WPF, que exibe as propriedades de uma árvore visual do objeto do WPF; e o visualizador de conjunto de dados, que funciona para objetos de DataSet, DataView e DataTable. Visualizadores adicionais podem estar disponíveis para download da Microsoft Corporation no futuro e estão disponíveis por meio de terceiros e da comunidade. Além disso, você pode escrever seus próprios visualizadores e instalá-los no [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] depurador.  
  
> [!NOTE]
> Nos aplicativos da **Store** , há suporte apenas para os visualizadores de texto padrão, HTML, XML e JSON. Não há suporte para visualizadores personalizados (criados pelo usuário).  
  
 Os visualizadores são representados no depurador por um ícone de lupa. Quando você vir o ícone de lupa em um **DataTip**, em uma janela variáveis do depurador ou na caixa de diálogo **QuickWatch** , você pode clicar na lupa para selecionar um visualizador apropriado para o tipo de dados do objeto correspondente.  
  
 Os visualizadores não têm suporte na Compact Framework.  
  
> [!NOTE]
> Os visualizadores do depurador exigem privilégios maiores do que são permitidos por um aplicativo de confiança parcial. Como resultado disso, os visualizadores não serão carregados quando você for interrompido no código com confiança parcial. Para depurar usando um visualizador, você deverá executar o código com confiança total.  
  
## <a name="in-this-section"></a>Nesta seção  
 [Como escrever um visualizador](../debugger/how-to-write-a-visualizer.md)  
  
 [Walkthrough: escrevendo um visualizador em C #](../debugger/walkthrough-writing-a-visualizer-in-csharp.md)  
  
 [Como instalar um visualizador](../debugger/how-to-install-a-visualizer.md)  
  
 [Como: testar e depurar um visualizador](../debugger/how-to-test-and-debug-a-visualizer.md)  
  
 [Referência de API do visualizador](../debugger/visualizer-api-reference.md)  
  
## <a name="related-sections"></a>Seções relacionadas  
 [Exibindo dados no depurador](../debugger/viewing-data-in-the-debugger.md)
