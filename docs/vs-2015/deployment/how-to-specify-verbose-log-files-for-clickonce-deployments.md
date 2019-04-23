---
title: 'Como: Especificar arquivos de Log detalhados para implantações do ClickOnce | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- logs, ClickOnce deployment
- ClickOnce deployment, logging
ms.assetid: 0807a28d-2e40-4a51-ab10-308d808ded6b
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: e200d0918e3d346f71da6ec2184e07e7d8433174
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/22/2019
ms.locfileid: "60069764"
---
# <a name="how-to-specify-verbose-log-files-for-clickonce-deployments"></a>Como: Especificar arquivos de log detalhados para implantações do ClickOnce
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] mantém os arquivos de log de atividades para todas as implantações. Esses logs documentar detalhes referentes à instalação, inicializando, atualizando e desinstalando uma [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] implantação. Para aumentar o detalhe que [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] gravações para esses arquivos de log, use o Editor do registro (**regedit.exe**) para especificar o nível de detalhamento.  
  
> [!CAUTION]
>  Se você usar o Editor do Registro incorretamente, poderá causar sérios problemas que talvez exijam a reinstalação do sistema operacional. Use o Editor do Registro por sua conta e risco.  
  
 O procedimento a seguir descreve como especificar o nível de detalhamento para [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] arquivos de log para o usuário atual. Para reduzir o nível de detalhamento, remova esse valor do registro.  
  
### <a name="to-specify-verbose-log-files"></a>Para especificar os arquivos de log detalhados  
  
1. Abra **Regedit.exe**.  
  
2. Navegue até o nó `HKEY_CURRENT_USER\Software\Classes\Software\Microsoft\Windows\CurrentVersion\Deployment`.  
  
3. Se necessário, crie um novo valor de cadeia de caracteres chamado `LogVerbosityLevel`.  
  
4. Defina as `LogVerbosityLevel` valor `1`.  
  
## <a name="see-also"></a>Consulte também  
 [Solução de problemas de implantações ClickOnce](../deployment/troubleshooting-clickonce-deployments.md)
