---
title: -ResetSettings (devenv.exe) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- Devenv, /ResetSettings switch
- ResetSettings switch
- /ResetSettings Devenv switch
ms.assetid: 1d41021c-6f58-4bd5-b122-d1c995812192
caps.latest.revision: 14
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 41e402a9268acecb70c83e26bab0e682d4ec59f5
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72665589"
---
# <a name="resetsettings-devenvexe"></a>/ResetSettings (devenv.exe)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Restaura [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] configurações padrão e inicia automaticamente o IDE do [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]. Opcionalmente, redefine as configurações para o arquivo .vssettings especificado.

 As configurações padrão são determinadas pelo perfil selecionado quando [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] foi inicializado pela primeira vez.

## <a name="syntax"></a>Sintaxe

```
Devenv /ResetSettings SettingsFile
```

## <a name="arguments"></a>Argumentos
 `SettingsFile` O caminho completo e o nome do arquivo .vssettings a ser aplicado a [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)].

 Para restaurar o perfil de Configurações Gerais de Desenvolvimento, use `General`.

## <a name="remarks"></a>Comentários
 Se nenhum `SettingsFile` for especificado, será solicitado que você selecione uma coleção padrão de configurações na próxima vez iniciar [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)].

## <a name="example"></a>Exemplo
 A seguinte linha de comando aplica as configurações armazenadas no arquivo `MySettings.vssettings`.

```
Devenv.exe /ResetSettings "C:\My Files\MySettings.vssettings"
```

## <a name="see-also"></a>Consulte Também
 [Personalizando as configurações de desenvolvimento nas opções de linha de comando do devenv do Visual Studio](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3) [Devenv Command Line Switches](../../ide/reference/devenv-command-line-switches.md)
