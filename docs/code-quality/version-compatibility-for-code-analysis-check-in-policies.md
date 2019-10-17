---
title: Compatibilidade da versão para políticas de check-in de análise do código
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- version compatibility, code analysis check-in policy
- check-in policies, version compatibility for code analysis
ms.assetid: 1af376e3-3be7-4445-803b-76a858567a5b
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c233d174922c0853d771356e0b68185c51c368ea
ms.sourcegitcommit: 485ffaedb1ade71490f11cf05962add1718945cc
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72448729"
---
# <a name="version-compatibility-for-code-analysis-check-in-policies"></a>Compatibilidade da versão para políticas de check-in de análise do código

Se você precisar avaliar e criar políticas de check-in de análise de código usando diferentes versões do [!INCLUDE[esprtfc](../code-quality/includes/esprtfc_md.md)], você deve saber as diferenças em como [!INCLUDE[vstsTfsOrcasLong](../code-quality/includes/vststfsorcaslong_md.md)] e [!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)] avaliam as políticas de check-in.

## <a name="version-compatibility-for-evaluating-check-in-policies"></a>Compatibilidade de versão para avaliar as políticas de check-in

- Quando as políticas de check-in de análise de código são avaliadas no [!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)], todas as regras que existiam no [!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)], mas que não existem no [!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)], são ignoradas.

- Quando as políticas de check-in de análise de código são avaliadas em [!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)], todas as novas regras que são exclusivas para [!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)] são ignoradas.

- Se a política de check-in da análise de código especificar assemblies de regras, [!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)] ignorará todas as regras que são especificadas por assemblies que ele não reconhece.

- Se a política de check-in da análise de código especificar assemblies de regras que [!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)] não reconhece, será exibida uma mensagem.

## <a name="version-compatibility-for-authoring-check-in-policies"></a>Compatibilidade de versão para criação de políticas de check-in

- Se você criou uma política de check-in de análise de código usando a versão [!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)] do [!INCLUDE[esprtfc](../code-quality/includes/esprtfc_md.md)], não poderá usar a versão [!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)] do [!INCLUDE[esprtfc](../code-quality/includes/esprtfc_md.md)] para modificá-la. Além disso, [!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)] não pode avaliar a política.

- Se você criou uma política de check-in de análise de código usando [!INCLUDE[esprtfc](../code-quality/includes/esprtfc_md.md)] em [!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)], você pode usar [!INCLUDE[esprtfc](../code-quality/includes/esprtfc_md.md)] no [!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)] para modificá-lo e a política também pode ser avaliada por [!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)]. Depois de modificar a política usando [!INCLUDE[esprtfc](../code-quality/includes/esprtfc_md.md)] em [!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)], você não poderá mais editar a política usando [!INCLUDE[esprtfc](../code-quality/includes/esprtfc_md.md)] em [!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)]. [!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)] pode avaliar as políticas sem problemas com nomes fortes incompatíveis.

- Para criar uma política de check-in de análise de código com configurações de regra que se aplicam a [!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)] e [!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)], você deve criar a política no [!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)], fazer todas as alterações necessárias e salvar a política. Se as alterações nas regras existirem somente no [!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)], você modificará e salvará a política em [!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)].

   Depois de salvar a política no [!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)], você não poderá mais alterar as configurações de regras que existem somente no [!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)].
