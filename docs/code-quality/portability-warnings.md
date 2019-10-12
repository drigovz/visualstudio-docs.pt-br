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
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 072858a9faafe312fd7c8314e7f25cf581c40844
ms.sourcegitcommit: e95dd8cedcd180e0bce6a75c86cf861757918290
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/09/2019
ms.locfileid: "72163066"
---
# <a name="portability-warnings"></a>Avisos de portabilidade
Os avisos de portabilidade dão suporte à portabilidade em diferentes sistemas operacionais.

## <a name="in-this-section"></a>Nesta seção

|Regra|Descrição|
|----------|-----------------|
|[CA1900: Os campos de tipo de valor devem ser portáteis @ no__t-0|Essa regra verifica se as estruturas declaradas usando um atributo de layout explícito serão alinhadas corretamente quando marshaled para código não gerenciado em sistemas operacionais de 64 bits.|
|[CA1901: As declarações P/Invoke devem ser portáteis @ no__t-0|Essa regra avalia o tamanho de cada parâmetro e o valor de retorno de um P/Invoke e verifica se seu tamanho está correto quando realizado marshaling em código não gerenciado em sistemas operacionais de 32 bits e 64 bits.|
|[CA1903: Usar somente a API da estrutura de destino @ no__t-0|Um membro ou um tipo está usando um membro ou um tipo que foi introduzido em um service pack não incluído com a estrutura de destino do projeto.|
