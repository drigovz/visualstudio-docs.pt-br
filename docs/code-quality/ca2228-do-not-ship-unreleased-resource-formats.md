---
title: 'CA2228: Não fornecer formatos de recurso não lançados'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- DoNotShipUnreleasedResourceFormats
- CA2228
helpviewer_keywords:
- CA2228
- DoNotShipUnreleasedResourceFormats
ms.assetid: 2c614edc-4e94-4b4f-8067-eea677a75cd9
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b3c6298c2186b6a73b4a7ef441b5f4c42c90ff6a
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2019
ms.locfileid: "71231057"
---
# <a name="ca2228-do-not-ship-unreleased-resource-formats"></a>CA2228: Não fornecer formatos de recurso não lançados

|||
|-|-|
|NomeDoTipo|DoNotShipUnreleasedResourceFormats|
|CheckId|CA2228|
|Categoria|Microsoft.Usage|
|Alteração significativa|Sem interrupção|

## <a name="cause"></a>Causa

Um arquivo de recurso foi criado usando uma versão do .NET que não tem suporte no momento.

## <a name="rule-description"></a>Descrição da regra

Os arquivos de recursos criados usando versões de pré-lançamento do .NET podem não ser utilizáveis por versões do .NET com suporte.

## <a name="how-to-fix-violations"></a>Como corrigir violações

Para corrigir uma violação dessa regra, compile o recurso usando uma versão com suporte do .NET.

## <a name="when-to-suppress-warnings"></a>Quando suprimir avisos

Não suprima um aviso nessa regra.
