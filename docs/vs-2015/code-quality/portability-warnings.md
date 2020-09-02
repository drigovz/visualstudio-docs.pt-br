---
title: Avisos de portabilidade | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- vs.codeanalysis.PortabilityRules
helpviewer_keywords:
- portability warnings
- managed code analysis warnings, portability warnings
- warnings, portability
ms.assetid: 902e859a-2153-4970-baaa-8a5b4a11806f
caps.latest.revision: 20
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 932474143b4770e81d8bfca14ab05a6538ae84a8
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72671164"
---
# <a name="portability-warnings"></a>Avisos de portabilidade
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Os avisos de portabilidade dão suporte à portabilidade em diferentes sistemas operacionais.

## <a name="in-this-section"></a>Nesta seção

|Regra|Descrição|
|----------|-----------------|
|[CA1900: Campos de tipo de valor devem ser portáteis](../code-quality/ca1900-value-type-fields-should-be-portable.md)|Essa regra verifica se as estruturas declaradas usando um atributo de layout explícito serão alinhadas corretamente quando marshaled para código não gerenciado em sistemas operacionais de 64 bits.|
|[CA1901: as declarações P/Invoke devem ser portáteis](../code-quality/ca1901-p-invoke-declarations-should-be-portable.md)|Essa regra avalia o tamanho de cada parâmetro e o valor de retorno de um P/Invoke e verifica se seu tamanho está correto quando realizado marshaling em código não gerenciado em sistemas operacionais de 32 bits e 64 bits.|
|[CA1903: Usar apenas a API da estrutura de destino](../code-quality/ca1903-use-only-api-from-targeted-framework.md)|Um membro ou um tipo está usando um membro ou um tipo que foi introduzido em um service pack não incluído com a estrutura de destino do projeto.|
