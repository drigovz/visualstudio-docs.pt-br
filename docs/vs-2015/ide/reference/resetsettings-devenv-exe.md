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
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 60e0dd272bd22cce2367e59b16fdea7965cb50e7
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MTE95
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54761583"
---
# <a name="resetsettings-devenvexe"></a>/ResetSettings (devenv.exe)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

  
Restaura [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] configurações padrão e inicia automaticamente o IDE do [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]. Opcionalmente, redefine as configurações para o arquivo .vssettings especificado.  
  
 As configurações padrão são determinadas pelo perfil selecionado quando [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] foi inicializado pela primeira vez.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
Devenv /ResetSettings SettingsFile  
```  
  
## <a name="arguments"></a>Arguments  
 `SettingsFile`  
 O caminho completo e o nome do arquivo .vssettings para aplicar a [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)].  
  
 Para restaurar o perfil de Configurações Gerais de Desenvolvimento, use `General`.  
  
## <a name="remarks"></a>Comentários  
 Se nenhum `SettingsFile` for especificado, será solicitado que você selecione uma coleção padrão de configurações na próxima vez iniciar [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)].  
  
## <a name="example"></a>Exemplo  
 A seguinte linha de comando aplica as configurações armazenadas no arquivo `MySettings.vssettings`.  
  
```  
Devenv.exe /ResetSettings "C:\My Files\MySettings.vssettings"  
```  
  
## <a name="see-also"></a>Consulte também  
 [Personalizando configurações de desenvolvimento no Visual Studio](http://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3)   
 [Opções de linha de comando devenv](../../ide/reference/devenv-command-line-switches.md)
