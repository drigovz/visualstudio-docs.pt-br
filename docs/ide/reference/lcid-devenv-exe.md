---
title: -LCID (devenv.exe)
ms.date: 12/10/2018
ms.prod: visual-studio-dev15
ms.topic: reference
helpviewer_keywords:
- language default
- locale IDs, setting for IDE
- Devenv, /L switch
- Devenv, /LCID switch
- locale IDs
- L Devenv switch
- /L Devenv switch
- LCID devenv switch
- /LCID Devenv switch
ms.assetid: 3a3f4e70-ea66-4351-9d62-acb1dec30e8e
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 42da279a64f04bca7775440f803e7a26e6bd2dc8
ms.sourcegitcommit: 01185dadd2fa1f9a040d2a366869f1a5e1d18e0f
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/11/2019
ms.locfileid: "54227298"
---
# <a name="lcid-devenvexe"></a>/LCID (devenv.exe)

Define o idioma padrão usado para texto, moeda e outros valores dentro do IDE.

## <a name="syntax"></a>Sintaxe

```shell
devenv {/LCID|/L} LocaleID
```

## <a name="arguments"></a>Arguments

- *LocaleID*

  Necessário. O identificador de localidade (LCID) do idioma que você especificar.

## <a name="remarks"></a>Comentários

Carrega o IDE e define o idioma natural padrão do ambiente. Essa alteração é mantida entre as sessões, e o IDE mostra essa alteração na caixa **Ferramentas** > **Opções** > **Ambiente**  >  **Configurações internacionais** > **Idioma**.

Se o idioma especificado não estiver disponível em seu sistema, a opção `/LCID` será ignorada.

A tabela a seguir lista os LCIDs dos idiomas para os quais o Visual Studio oferece suporte.

|Idioma|LCID|
|--------------|----------|
|Chinês (simplificado)|2052|
|Chinês (tradicional)|1028|
|Inglês|1033|
|Francês|1036|
|Alemão|1031|
|Italiano|1040|
|Japonês|1041|
|Coreano|1042|
|Espanhol|3082|

## <a name="example"></a>Exemplo

Este exemplo carrega o IDE com cadeias de caracteres de recursos em inglês.

```shell
devenv /LCID 1033
```

## <a name="see-also"></a>Consulte também

- [Opções de linha de comando do Devenv](../../ide/reference/devenv-command-line-switches.md)
- [Caixa de diálogo Configurações Internacionais, Ambiente, Opções](../../ide/reference/international-settings-environment-options-dialog-box.md)
- [Personalizando layouts de janela](../../ide/customizing-window-layouts-in-visual-studio.md)