---
title: -LCID (devenv.exe)
ms.date: 12/10/2018
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
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 80c4af137edc80166d6a652c676d5607d8c2328d
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/01/2020
ms.locfileid: "75595521"
---
# <a name="lcid-devenvexe"></a>/LCID (devenv.exe)

Define o idioma padrão usado para texto, moeda e outros valores dentro do IDE.

## <a name="syntax"></a>Sintaxe

```shell
devenv {/LCID|/L} LocaleID
```

## <a name="arguments"></a>Arguments

- *LocaleID*

  Necessária. O identificador de localidade (LCID) do idioma que você especificar.

## <a name="remarks"></a>Comentários

Carrega o IDE e define o idioma natural padrão do ambiente. Essa alteração é mantida entre as sessões, e o IDE mostra essa alteração na caixa **Ferramentas** > **Opções** > **Ambiente** > **Configurações internacionais** > **Idioma**.

Se o idioma especificado não estiver disponível em seu sistema, a opção `/LCID` será ignorada.

A tabela a seguir lista os LCIDs dos idiomas para os quais o Visual Studio oferece suporte.

|{1&gt;Idioma&lt;1}|LCID|
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

## <a name="see-also"></a>Veja também

- [Opções de linha de comando do Devenv](../../ide/reference/devenv-command-line-switches.md)
- [Caixa de diálogo Configurações Internacionais, Ambiente, Opções](../../ide/reference/international-settings-environment-options-dialog-box.md)
- [Personalizando layouts de janela](../../ide/customizing-window-layouts-in-visual-studio.md)
