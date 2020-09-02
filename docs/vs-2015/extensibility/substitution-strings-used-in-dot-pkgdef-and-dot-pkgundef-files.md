---
title: Cadeias de caracteres de substituição usadas no. Pkgdef e. Arquivos Pkgundef | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio shell, isolated mode%2C .pkgdef and .pkgundef files
ms.assetid: b1755d63-d794-4fd7-864b-70a9684881c2
caps.latest.revision: 5
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 47434d9d1dfcedeeaea330b1d65645d7a632c6e6
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68160542"
---
# <a name="substitution-strings-used-in-pkgdef-and-pkgundef-files"></a>Cadeias substituição usadas em arquivos .Pkgdef e .Pkgundef
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Você pode usar as cadeias de caracteres de substituição listadas abaixo nos arquivos. pkgdef e. pkgundef que você define para o aplicativo de shell isolado do Visual Studio.  
  
## <a name="substitution-strings"></a>Cadeias de caracteres de substituição  
  
|String|Descrição|  
|------------|-----------------|  
|$=*RegistryEntry*$|O valor da entrada *RegistryEntry* . Se a cadeia de caracteres de entrada do registro terminar em uma barra invertida ( \\ ), o valor padrão da subchave do registro será usado. Por exemplo, a cadeia de caracteres de substituição $ = HKEY_CURRENT_USER \Environment\TEMP $ é expandida para a pasta temporária do usuário atual.|  
|$AppName $|O nome qualificado do aplicativo que é passado para os pontos de entrada de AppEnv.dll. O nome qualificado consiste no nome do aplicativo, um sublinhado e o identificador de classe (CLSID) do objeto de automação do aplicativo, que também é registrado como o valor da configuração ThisVersionDTECLSID no arquivo Project. pkgdef.|  
|$AppDataLocalFolder|A subpasta em% LOCALAPPDATA% para este aplicativo.|  
|$BaseInstallDir $|O caminho completo do local onde o Visual Studio foi instalado.|  
|$CommonFiles $|O valor da variável de ambiente% CommonProgramFiles%.|  
|$MyDocuments $|O caminho completo da pasta meus documentos do usuário atual.|  
|$PackageFolder $|O caminho completo do diretório que contém os arquivos de assembly do pacote para o aplicativo.|  
|$ProgramFiles $|O valor da variável de ambiente% ProgramFiles%.|  
|$RootFolder $|O caminho completo do diretório raiz do aplicativo.|  
|$RootKey $|A chave do registro raiz para o aplicativo. Por padrão, a raiz está no HKEY_CURRENT_USER \Software \\ *CompanyName* \\ *ProjectName* \\ *versionNumber* (quando o aplicativo está em execução, _Config é acrescentado a essa chave). Ele é definido pelo valor RegistryRoot no arquivo *SolutionName*. pkgdef.<br /><br /> O $RootKey $ String pode ser usado para recuperar um valor de registro na subchave do aplicativo. Por exemplo, a cadeia de caracteres "$ = $RootKey $ \AppIcon $" retornará o valor da entrada AppIcon na subchave raiz do aplicativo.<br /><br /> O analisador processa o arquivo. pkgdef sequencialmente e pode acessar uma entrada de registro na subchave do aplicativo somente se a entrada tiver sido definida anteriormente|  
|$ShellFolder $|O caminho completo do local onde o Visual Studio foi instalado.|  
|$System $|A pasta Windows\system32.|  
|$WINDIR $|A pasta do Windows.|  
  
 Se o analisador não reconhecer a cadeia de caracteres de substituição ou não puder determinar o valor de uma entrada de registro ou de uma variável de ambiente, ele não executará a substituição nessa parte da cadeia de caracteres.
