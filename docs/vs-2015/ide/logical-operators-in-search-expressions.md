---
title: Operadores lógicos em expressões de pesquisa | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- Help Viewer 2.0, logical operators in search
- logical operators in search [Help Viewer 2.0]
ms.assetid: 0c38ae7d-3e20-4d47-a020-9677cd285916
caps.latest.revision: 11
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 66d6aa6a11ef0ce308c5ba2b089aaa8170b6441f
ms.sourcegitcommit: a83c60bb00bf95e6bea037f0e1b9696c64deda3c
ms.translationtype: MTE95
ms.contentlocale: pt-BR
ms.lasthandoff: 02/19/2019
ms.locfileid: "54760064"
---
# <a name="logical-operators-in-search-expressions"></a>Operadores lógicos em expressões de pesquisa
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Usando operadores lógicos, você pode refinar a pesquisa de conteúdo criando expressões de pesquisa mais complicadas desde mais simples. Como mostra a tabela a seguir, os operadores lógicos especificam como vários termos de pesquisa devem ser combinados em uma consulta de pesquisa.  
  
> [!IMPORTANT]
>  Você deve inserir os operadores lógicos em letras maiúsculas para o mecanismo de pesquisa reconhecê-los.  
  
|Para pesquisar|Use|Exemplo|Resultado|  
|-------------------|---------|-------------|------------|  
|Ambos os termos no mesmo tópico|AND|dib AND paleta|Tópicos que contêm "dib" e "paleta".|  
|Um dos dois termos em um tópico|OU|varredura OR vetor|Tópicos que contêm "varredura" ou "vetor".|  
|Primeiro termo sem um segundo termo no mesmo tópico|NOT|"operating system" NOT DOS|Tópicos que contêm "sistema operacional", mas não "DOS".|  
|Os dois termos, próximos em um tópico|PRÓXIMO|usuário NEAR kernel|Tópicos que contêm "usuário" bastante próximo de "kernel".|  
  
## <a name="see-also"></a>Consulte também  
 [Dicas de pesquisa de texto completo](../ide/full-text-search-tips.md)   
 [Localizar informações](../ide/locate-information.md)
