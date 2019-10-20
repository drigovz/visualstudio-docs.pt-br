---
title: Compatibilidade de versão para políticas de check-in de análise de código | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
helpviewer_keywords:
- version compatibility, code analysis check-in policy
- check-in policies, version compatibility for code analysis
ms.assetid: 1af376e3-3be7-4445-803b-76a858567a5b
caps.latest.revision: 17
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 075981569cbee05e90afe17b3afc9558d7bbb270
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72609313"
---
# <a name="version-compatibility-for-code-analysis-check-in-policies"></a>Compatibilidade da versão para políticas de check-in de análise do código
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Se você precisar avaliar e criar políticas de check-in de análise de código usando diferentes versões do [!INCLUDE[esprtfc](../includes/esprtfc-md.md)], você deve saber as diferenças em como [!INCLUDE[vstsTfsOrcasLong](../includes/vststfsorcaslong-md.md)] e [!INCLUDE[vstsTfsRosarioShort](../includes/vststfsrosarioshort-md.md)] avaliar as políticas de check-in.

## <a name="version-compatibility-for-evaluating-check-in-policies"></a>Compatibilidade de versão para avaliar as políticas de check-in

- Quando as políticas de check-in de análise de código são avaliadas em [!INCLUDE[vstsTfsOrcasShort](../includes/vststfsorcasshort-md.md)], todas as regras que existiam no [!INCLUDE[vstsTfsRosarioShort](../includes/vststfsrosarioshort-md.md)] mas que não existem em [!INCLUDE[vstsTfsOrcasShort](../includes/vststfsorcasshort-md.md)] são ignoradas.

- Quando as políticas de check-in de análise de código são avaliadas em [!INCLUDE[vstsTfsRosarioShort](../includes/vststfsrosarioshort-md.md)], todas as novas regras que são exclusivas para [!INCLUDE[vstsTfsOrcasShort](../includes/vststfsorcasshort-md.md)] são ignoradas.

- Se a política de check-in da análise de código especificar assemblies de regras, [!INCLUDE[vstsTfsOrcasShort](../includes/vststfsorcasshort-md.md)] ignorará todas as regras que são especificadas por assemblies que ele não reconhece.

- Se a política de check-in da análise de código especificar assemblies de regras que [!INCLUDE[vstsTfsRosarioShort](../includes/vststfsrosarioshort-md.md)] não reconhece, será exibida uma mensagem.

## <a name="version-compatibility-for-authoring-check-in-policies"></a>Compatibilidade de versão para criação de políticas de check-in

- Se você criou uma política de check-in de análise de código usando a versão [!INCLUDE[vstsTfsOrcasShort](../includes/vststfsorcasshort-md.md)] do [!INCLUDE[esprtfc](../includes/esprtfc-md.md)], não será possível usar a versão [!INCLUDE[vstsTfsRosarioShort](../includes/vststfsrosarioshort-md.md)] do [!INCLUDE[esprtfc](../includes/esprtfc-md.md)] para modificá-la. Além disso, [!INCLUDE[vstsTfsRosarioShort](../includes/vststfsrosarioshort-md.md)] não pode avaliar a política.

- Se você criou uma política de check-in de análise de código usando [!INCLUDE[esprtfc](../includes/esprtfc-md.md)] em [!INCLUDE[vstsTfsRosarioShort](../includes/vststfsrosarioshort-md.md)], você pode usar [!INCLUDE[esprtfc](../includes/esprtfc-md.md)] no [!INCLUDE[vstsTfsOrcasShort](../includes/vststfsorcasshort-md.md)] para modificá-la e a política também pode ser avaliada pelo [!INCLUDE[vstsTfsOrcasShort](../includes/vststfsorcasshort-md.md)]. Depois de modificar a política usando [!INCLUDE[esprtfc](../includes/esprtfc-md.md)] em [!INCLUDE[vstsTfsOrcasShort](../includes/vststfsorcasshort-md.md)], você não poderá mais editar a política usando [!INCLUDE[esprtfc](../includes/esprtfc-md.md)] no [!INCLUDE[vstsTfsRosarioShort](../includes/vststfsrosarioshort-md.md)]. [!INCLUDE[vstsTfsRosarioShort](../includes/vststfsrosarioshort-md.md)] pode avaliar as políticas sem problemas com nomes fortes incompatíveis.

- Para criar uma política de check-in de análise de código com as configurações de regra que se aplicam para [!INCLUDE[vstsTfsRosarioShort](../includes/vststfsrosarioshort-md.md)] e [!INCLUDE[vstsTfsOrcasShort](../includes/vststfsorcasshort-md.md)], você deve criar a política em [!INCLUDE[vstsTfsRosarioShort](../includes/vststfsrosarioshort-md.md)], fazer todas as alterações necessárias e salvar a política. Se as alterações nas regras existirem somente no [!INCLUDE[vstsTfsOrcasShort](../includes/vststfsorcasshort-md.md)], você modificará e salvará a política em [!INCLUDE[vstsTfsOrcasShort](../includes/vststfsorcasshort-md.md)].

     Depois de salvar a política no [!INCLUDE[vstsTfsOrcasShort](../includes/vststfsorcasshort-md.md)], você não poderá mais alterar as configurações de regras que existem somente no [!INCLUDE[vstsTfsRosarioShort](../includes/vststfsrosarioshort-md.md)].
