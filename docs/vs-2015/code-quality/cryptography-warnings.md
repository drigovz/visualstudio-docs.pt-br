---
title: Avisos de criptografia | Microsoft Docs
ms.date: 11/15/2016
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
ms.assetid: d96723ea-a293-488d-b9db-adb437e50cdd
caps.latest.revision: 9
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: c573d461b477bbcdc7e988ea66f03d5a7cc0fdb6
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68201442"
---
# <a name="cryptography-warnings"></a>Avisos de criptografia
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Avisos de criptografia dão suporte a mais segura de bibliotecas e aplicativos por meio do uso correto da criptografia. Esses avisos ajudam a evitar falhas de segurança em seu programa. Se você desabilitar um desses avisos, você deve marcar claramente a razão no código e também informar o agente de segurança designado para seu projeto de desenvolvimento.  
  
|Regra|Descrição|  
|----------|-----------------|  
|[CA5350: Não Use algoritmos criptográficos fracos](../code-quality/ca5350-do-not-use-weak-cryptographic-algorithms.md)|Algoritmos de criptografia fraca e funções de hash são usadas atualmente por uma série de motivos, mas não deve ser usados para garantir a confidencialidade ou a integridade dos dados que eles protegem.        Essa regra dispara quando ele encontra algoritmos TripleDES, SHA1 ou RIPEMD160 no código.|  
|[CA5351: não usar algoritmos criptográficos desfeitos](../code-quality/ca5351-do-not-use-broken-cryptographic-algorithms.md)|Dividido criptográfico algoritmos não são considerados seguros e seu uso deve ser altamente desaconselhável. Essa regra dispara quando ele encontra o algoritmo de hash MD5 ou DES ou RC2 algoritmos de criptografia no código.|
