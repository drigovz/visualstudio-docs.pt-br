---
title: Avisos de portabilidade
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.codeanalysis.PortabilityRules
helpviewer_keywords:
- portability warnings
- managed code analysis warnings, portability warnings
- warnings, portability
ms.assetid: 902e859a-2153-4970-baaa-8a5b4a11806f
author: jillre
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 61efbc2022b2c0cd60e005936e148bbaf1d900a4
ms.sourcegitcommit: 00ba14d9c20224319a5e93dfc1e0d48d643a5fcd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2020
ms.locfileid: "77091724"
---
# <a name="portability-warnings"></a>Avisos de portabilidade
Os avisos de portabilidade dão suporte à portabilidade em diferentes sistemas operacionais.

## <a name="in-this-section"></a>Nesta seção

|Regra|Descrição|
|----------|-----------------|
|[CA1900: os campos de tipo de valor devem ser móveis](../code-quality/ca1900.md)|Essa regra verifica se as estruturas declaradas usando um atributo de layout explícito serão alinhadas corretamente quando marshaled para código não gerenciado em sistemas operacionais de 64 bits.|
|[CA1901: as declarações P/Invoke devem ser portáteis](../code-quality/ca1901.md)|Essa regra avalia o tamanho de cada parâmetro e o valor de retorno de um P/Invoke e verifica se seu tamanho está correto quando realizado marshaling em código não gerenciado em sistemas operacionais de 32 bits e 64 bits.|
|[CA1903: usar apenas a API da estrutura de destino](../code-quality/ca1903.md)|Um membro ou um tipo está usando um membro ou um tipo que foi introduzido em um service pack não incluído com a estrutura de destino do projeto.|
