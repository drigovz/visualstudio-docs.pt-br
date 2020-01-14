---
title: Avisos de criptografia
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: d96723ea-a293-488d-b9db-adb437e50cdd
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 78923dfd2873b53790421cde3fe01f024e267202
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/01/2020
ms.locfileid: "75587687"
---
# <a name="cryptography-warnings"></a>Avisos de criptografia
Os avisos de criptografia dão suporte a bibliotecas e aplicativos mais seguros por meio do uso correto de criptografia. Esses avisos ajudam a evitar falhas de segurança em seu programa. Se você desabilitar um desses avisos, você deve marcar claramente a razão no código e também informar o agente de segurança designado para seu projeto de desenvolvimento.

|Regra|Descrição|
|----------|-----------------|
|[CA5350: não usar algoritmos criptográficos fracos](../code-quality/ca5350.md)|Algoritmos de criptografia fracos e funções de hash são usados hoje por vários motivos, mas eles não devem ser usados para garantir a confidencialidade ou a integridade dos dados que eles protegem.        Essa regra é disparada quando encontra algoritmos TripleDES, SHA1 ou RIPEMD160 no código.|
|[CA5351: não usar algoritmos criptográficos desfeitos](../code-quality/ca5351.md)|Os algoritmos de criptografia desfeitos não são considerados seguros e seu uso deve ser altamente desencorajado. Essa regra é disparada quando encontra o algoritmo de hash MD5 ou os algoritmos de criptografia DES ou RC2 no código.|
