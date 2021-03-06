---
title: Compatibilidade da versão para políticas de check-in de análise do código
ms.date: 11/04/2016
description: Saiba como o Team System 2008 Team Foundation Server e Team Foundation Server 2010 avaliar as políticas de check-in do Visual Studio de forma diferente.
ms.custom: SEO-VS-2020
ms.topic: conceptual
helpviewer_keywords:
- version compatibility, code analysis check-in policy
- check-in policies, version compatibility for code analysis
ms.assetid: 1af376e3-3be7-4445-803b-76a858567a5b
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 24a97e9175e75d8018aff269066f13a796e1cf64
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99867666"
---
# <a name="version-compatibility-for-code-analysis-check-in-policies"></a>Compatibilidade da versão para políticas de check-in de análise do código

Se você precisar avaliar e criar políticas de check-in de análise de código usando versões diferentes do [!INCLUDE[esprtfc](../code-quality/includes/esprtfc_md.md)] , você deve saber as diferenças em como [!INCLUDE[vstsTfsOrcasLong](../code-quality/includes/vststfsorcaslong_md.md)] avaliar as políticas de [!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)] check-in.

## <a name="version-compatibility-for-evaluating-check-in-policies"></a>Compatibilidade de versão para avaliar políticas de Check-In

- Quando as políticas de check-in de análise de código são avaliadas no [!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)] , todas as regras que existiam no [!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)] , mas não existem no, [!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)] são ignoradas.

- Quando as políticas de check-in de análise de código são avaliadas no [!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)] , todas as novas regras que são exclusivas para [!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)] são ignoradas.

- Se a política de check-in da análise de código especificar assemblies de regras, o [!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)] ignorará todas as regras que são especificadas por assemblies que ele não reconhece.

- Se a política de check-in da análise de código especificar assemblies de regras que não [!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)] reconhece, será exibida uma mensagem.

## <a name="version-compatibility-for-authoring-check-in-policies"></a>Compatibilidade de versão para criação de políticas de Check-In

- Se você criou uma política de check-in de análise de código usando a [!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)] versão do [!INCLUDE[esprtfc](../code-quality/includes/esprtfc_md.md)] , não poderá usar a [!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)] versão do [!INCLUDE[esprtfc](../code-quality/includes/esprtfc_md.md)] para modificá-la. Além disso, [!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)] o não pode avaliar a política.

- Se você criou uma política de check-in de análise de código usando o [!INCLUDE[esprtfc](../code-quality/includes/esprtfc_md.md)] no [!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)] , pode usar [!INCLUDE[esprtfc](../code-quality/includes/esprtfc_md.md)] [!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)] o no para modificá-la e a política também pode ser avaliada pelo [!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)] . Depois de modificar a política usando o [!INCLUDE[esprtfc](../code-quality/includes/esprtfc_md.md)] no [!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)] , você não poderá mais editar a política usando o [!INCLUDE[esprtfc](../code-quality/includes/esprtfc_md.md)] no [!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)] . [!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)] pode avaliar as políticas sem problemas com nomes fortes incompatíveis.

- Para criar uma política de check-in de análise de código com as configurações de regra que se aplicam ao [!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)] e ao [!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)] , você deve criar a política no [!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)] , fazer todas as alterações necessárias e salvar a política. Se as alterações nas regras existirem apenas no [!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)] , você modificará e salvará a política no [!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)] .

   Depois de salvar a política no [!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)] , você não poderá mais alterar as configurações de regras que existem [!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)] somente no.
