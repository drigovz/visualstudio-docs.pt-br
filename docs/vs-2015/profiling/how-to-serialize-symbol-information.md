---
title: 'Como: Serializar informações de símbolo | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- VS.ToolsOptionsPages.Performance.General
helpviewer_keywords:
- profiling tools, serializing symbol information
- performance tools, serializing symbol information
ms.assetid: 9e0da706-6325-4073-83d1-aeab3b7c137a
caps.latest.revision: 14
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: b29ddb0e88a58fbfd924c40134305cf33a3e170b
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/22/2019
ms.locfileid: "60103791"
---
# <a name="how-to-serialize-symbol-information"></a>Como: Serializar informações de símbolo
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Você pode serializar os símbolos que são necessários para analisar seu aplicativo. A serialização de símbolos adiciona símbolos no arquivo .vsp. Ao adicionar informações de símbolo no arquivo .vsp, outras pessoas podem analisar um relatório de desempenho sem ter acesso aos símbolos originais. Se os símbolos não forem serializados, você deverá ter os arquivos originais instrumentados .exe e .pdb para analisar o arquivo .vsp.  
  
### <a name="to-automatically-serialize-symbol-information"></a>Para serializar informações de símbolo automaticamente  
  
1. No menu **Ferramentas**, clique em **Opções**.  
  
     A caixa de diálogo **Opções** é exibida.  
  
2. Clique em **Ferramentas de Desempenho**.  
  
3. Em **Configuração Geral**, selecione **Serializar informações de símbolo automaticamente**.  
  
## <a name="see-also"></a>Consulte também  
 [Configurando sessões de desempenho](../profiling/configuring-performance-sessions.md)   
 [Como: Informações de símbolo do Windows de referência](../profiling/how-to-reference-windows-symbol-information.md)   
 [Como: Salvar arquivos de relatório analisados](http://msdn.microsoft.com/0340ddde-caf4-48ac-8af3-d15dcdade556)
