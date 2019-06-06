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
ms.openlocfilehash: 5f8a672056c8663c2e27ec730e542083aee9738f
ms.sourcegitcommit: 5483e399f14fb01f528b3b194474778fd6f59fa6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/05/2019
ms.locfileid: "66714986"
---
# <a name="ca2228-do-not-ship-unreleased-resource-formats"></a>CA2228: Não fornecer formatos de recurso não lançados

|||
|-|-|
|NomeDoTipo|DoNotShipUnreleasedResourceFormats|
|CheckId|CA2228|
|Categoria|Microsoft.Usage|
|Alteração Significativa|Não separável|

## <a name="cause"></a>Causa

Um arquivo de recurso foi criado usando uma versão do .NET que não é suportada atualmente.

## <a name="rule-description"></a>Descrição da regra

Arquivos de recursos que foram compilados usando versões de pré-lançamento do .NET não podem ser usados por versões com suporte do .NET.

## <a name="how-to-fix-violations"></a>Como corrigir violações

Para corrigir uma violação dessa regra, crie o recurso usando uma versão compatível do .NET.

## <a name="when-to-suppress-warnings"></a>Quando suprimir avisos

Não suprima um aviso nessa regra.
