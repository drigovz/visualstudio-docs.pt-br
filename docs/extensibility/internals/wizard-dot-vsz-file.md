---
title: Mago (. Vsz) Arquivo | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- .vsz files
- vsz files
- wizards, files
ms.assetid: 72e1d0f3-eef1-455e-b803-96827f030f50
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 0fedf409c0ca320c054ddf1cc16318d08d25463a
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80703317"
---
# <a name="wizard-vsz-file"></a>Arquivo do assistente (.Vsz)

O ambiente de desenvolvimento integrado (IDE) usa arquivos .vsz para iniciar assistentes. Esses arquivos .vsz contêm informações que o IDE usa para determinar qual assistente chamar e quais informações passar para o assistente.

Um arquivo .vsz é uma versão de um arquivo de texto formatado .ini que não tem seções. As informações conhecidas pelo IDE são armazenadas no início do arquivo. Isso fornece um link entre o assistente que o IDE chama e os parâmetros que estão no arquivo .vsz a serem passados para o IDE. O resto do arquivo fornece parâmetros específicos para o assistente e que devem ser coletados pelo IDE e passados para o assistente específico.

O exemplo a seguir mostra o conteúdo de um arquivo .vsz.

```
VSWizard 8.0
Wizard=VsWizard.CBlankSiteWizard -or- {123-1234556-123334}
Param="WIZARDNAME = Wizard One"
Param="WIZARDUI = FALSE"
```

A seguir estão as partes no arquivo .vsz.

|Parte|Descrição|
|----------|-----------------|
|Vswizard|O primeiro parâmetro no arquivo é o número da versão do formato do arquivo do modelo. Este número de versão deve ser 6.0, 7.0, 7.1 ou 8.0. Outros números não podem ser iniciados e causar um erro de formato inválido.|
|Assistente|Este campo contém o ProgID OLE do assistente, ou, alternativamente, uma representação de seqüência GUID do CLSID do assistente que é cocriado pelo IDE.|
|Param|Essas peças são opcionais. Você pode adicionar quantos necessário.|

Os parâmetros permitem que o arquivo .vsz passe parâmetros personalizados adicionais para o assistente. Cada valor é passado como um elemento de seqüência em uma matriz de variantes para o assistente. Para obter mais informações, consulte [Parâmetros personalizados](../../extensibility/internals/custom-parameters.md).

Para adicionar um ID local padrão ao seu `FALLBACK_LCID`arquivo .vsz, especifique =xxxx, onde xxxx é o ID local, por exemplo, 1033 para inglês. Quando `FALLBACK_LCID` o parâmetro é definido, o assistente usa o ID local de recuo fornecido se o ID atual não for encontrado.

## <a name="see-also"></a>Confira também

- [Parâmetros personalizados](../../extensibility/internals/custom-parameters.md)
- [Assistentes](../../extensibility/internals/wizards.md)
- [Arquivos de descrição do diretório de modelo (.Vsdir)](../../extensibility/internals/template-directory-description-dot-vsdir-files.md)
