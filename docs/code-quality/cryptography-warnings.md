---
title: Avisos de criptografia
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
ms.assetid: d96723ea-a293-488d-b9db-adb437e50cdd
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: bff3ffef284c0cbf1503d573ba01c7a88c1c5e95
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/02/2019
ms.locfileid: "53964170"
---
# <a name="cryptography-warnings"></a>Avisos de criptografia
Avisos de criptografia dão suporte a mais segura de bibliotecas e aplicativos por meio do uso correto da criptografia. Esses avisos ajudam a evitar falhas de segurança em seu programa. Se você desabilitar um desses avisos, você deve marcar claramente a razão no código e também informar o agente de segurança designado para seu projeto de desenvolvimento.

|Regra|Descrição|
|----------|-----------------|
|[CA5350: Não Use algoritmos criptográficos fracos](../code-quality/ca5350-do-not-use-weak-cryptographic-algorithms.md)|Algoritmos de criptografia fraca e funções de hash são usadas atualmente por uma série de motivos, mas não deve ser usados para garantir a confidencialidade ou a integridade dos dados que eles protegem.        Essa regra dispara quando ele encontra algoritmos TripleDES, SHA1 ou RIPEMD160 no código.|
|[CA5351: não usar algoritmos criptográficos desfeitos](../code-quality/ca5351-do-not-use-broken-cryptographic-algorithms.md)|Dividido criptográfico algoritmos não são considerados seguros e seu uso deve ser altamente desaconselhável. Essa regra dispara quando ele encontra o algoritmo de hash MD5 ou DES ou RC2 algoritmos de criptografia no código.|