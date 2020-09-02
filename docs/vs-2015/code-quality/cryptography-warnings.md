---
title: Avisos de criptografia | Microsoft Docs
ms.date: 11/15/2016
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
ms.assetid: d96723ea-a293-488d-b9db-adb437e50cdd
caps.latest.revision: 9
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: d9f5694ccf48615ebdf7157adc80543b0fbb71eb
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72667671"
---
# <a name="cryptography-warnings"></a>Avisos de criptografia
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Os avisos de criptografia dão suporte a bibliotecas e aplicativos mais seguros por meio do uso correto de criptografia. Esses avisos ajudam a evitar falhas de segurança em seu programa. Se você desabilitar um desses avisos, você deve marcar claramente a razão no código e também informar o agente de segurança designado para seu projeto de desenvolvimento.

|Regra|Descrição|
|----------|-----------------|
|[CA5350: Não usar algoritmos de criptografia fracos](../code-quality/ca5350-do-not-use-weak-cryptographic-algorithms.md)|Algoritmos de criptografia fracos e funções de hash são usados hoje por vários motivos, mas eles não devem ser usados para garantir a confidencialidade ou a integridade dos dados que eles protegem.        Essa regra é disparada quando encontra algoritmos TripleDES, SHA1 ou RIPEMD160 no código.|
|[CA5351 não use algoritmos de criptografia desfeitos](../code-quality/ca5351-do-not-use-broken-cryptographic-algorithms.md)|Os algoritmos de criptografia desfeitos não são considerados seguros e seu uso deve ser altamente desencorajado. Essa regra é disparada quando encontra o algoritmo de hash MD5 ou os algoritmos de criptografia DES ou RC2 no código.|
