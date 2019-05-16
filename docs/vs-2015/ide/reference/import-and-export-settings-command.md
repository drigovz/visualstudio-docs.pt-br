---
title: Comando Import and Export Settings | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- Tools.ImportandExportSettings
helpviewer_keywords:
- Tools.ImportandExportSettings
- Import and Export Settings command
ms.assetid: 94a06468-a44d-403d-a931-77bbc9d06e56
caps.latest.revision: 12
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 91b34183e36c86290c14e3da7d17687d45cfe180
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MTE95
ms.contentlocale: pt-BR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65694654"
---
# <a name="import-and-export-settings-command"></a>Comando Importar e Exportar Configurações
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Importa, exporta ou redefine configurações [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)].  
  
## <a name="syntax"></a>Sintaxe  
  
```  
Tools.ImportandExportSettings [/export:filename | /import:filename | /reset]  
```  
  
## <a name="switches"></a>Opções  
 /export:`filename`  
 Opcional. Exporta as configurações atuais para o arquivo especificado.  
  
 /import:`filename`  
 Opcional. Importa as configurações no arquivo especificado.  
  
 /reset  
 Opcional. Redefine as configurações atuais.  
  
## <a name="remarks"></a>Comentários  
 Executar esse comando sem nenhuma opção abre o assistente **Importar e Exportar Configurações**. Para obter mais informações, consulte [Como: Compartilhar configurações entre computadores ou versões de Visual Studio](https://msdn.microsoft.com/1131fb10-35c1-42da-9cd8-91aa3235b882).  
  
## <a name="example"></a>Exemplo  
 O comando a seguir exporta as configurações atuais para o arquivo `MyFile.vssettings`.  
  
```  
Tools.ImportandExportSettings /export:"c:\Files\MyFile.vssettings"  
```  
  
## <a name="see-also"></a>Consulte também  
 [Personalizando configurações de desenvolvimento no Visual Studio](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3)   
 [Comandos do Visual Studio](../../ide/reference/visual-studio-commands.md)
