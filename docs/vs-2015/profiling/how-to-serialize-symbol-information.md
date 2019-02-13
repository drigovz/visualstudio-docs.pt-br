---
title: Como serializar informações de símbolo | Microsoft Docs
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
ms.openlocfilehash: 3f0359613586531a4cc7b80e25acc02be9ae37f9
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MTE95
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54769166"
---
# <a name="how-to-serialize-symbol-information"></a>Como serializar informações de símbolo
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Você pode serializar os símbolos que são necessários para analisar seu aplicativo. A serialização de símbolos adiciona símbolos no arquivo .vsp. Ao adicionar informações de símbolo no arquivo .vsp, outras pessoas podem analisar um relatório de desempenho sem ter acesso aos símbolos originais. Se os símbolos não forem serializados, você deverá ter os arquivos originais instrumentados .exe e .pdb para analisar o arquivo .vsp.  
  
### <a name="to-automatically-serialize-symbol-information"></a>Para serializar informações de símbolo automaticamente  
  
1.  No menu **Ferramentas**, clique em **Opções**.  
  
     A caixa de diálogo **Opções** é exibida.  
  
2.  Clique em **Ferramentas de Desempenho**.  
  
3.  Em **Configuração Geral**, selecione **Serializar informações de símbolo automaticamente**.  
  
## <a name="see-also"></a>Consulte também  
 [Configurando sessões de desempenho](../profiling/configuring-performance-sessions.md)   
 [Como fazer referência a informações de símbolo do Windows](../profiling/how-to-reference-windows-symbol-information.md)   
 [Como salvar arquivos de relatório analisados](http://msdn.microsoft.com/0340ddde-caf4-48ac-8af3-d15dcdade556)
