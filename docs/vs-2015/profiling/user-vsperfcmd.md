---
title: Usuário (VSPerfCmd) | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ee1a478e-374d-4f30-ae28-d260b9d4723a
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b390852c94477a6b02d43b0dbc7678384c622ced
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49301990"
---
# <a name="user-vsperfcmd"></a>Usuário (VSPerfCmd)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

A opção **Usuário** especifica o domínio e o nome de usuário da conta que possui o processo com perfil. Esta opção é necessária apenas se o processo estiver sendo executado como um usuário diferente do usuário conectado. O proprietário do processo é listado na coluna Nome de Usuário na guia Processos do Gerenciador de Tarefas do Windows.  
  
 A opção **Usuário** só pode ser especificada em uma linha de comando que também contém a opção **Iniciar**.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
VSPerfCmd.exe /Start:Method /Output:FileName /User:[Domain\]UserName [Options]  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `Domain`  
 O nome do domínio do usuário.  
  
 `UserName`  
 O nome do usuário.  
  
## <a name="required-options"></a>Opções obrigatórias  
 A opção **Usuário** só pode ser usada com a opção **Iniciar**.  
  
 **Iniciar:** `Method`  
 Inicializa o criador de perfil para o método de criação de perfil especificado.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir demonstra o uso da opção **Usuário**.  
  
```  
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp /User:SYSTEM  
```  
  
## <a name="see-also"></a>Consulte também  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [Criando perfil de aplicativos autônomos](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Criando perfil de aplicativos Web ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Serviços de Criação de Perfil](../profiling/command-line-profiling-of-services.md)



