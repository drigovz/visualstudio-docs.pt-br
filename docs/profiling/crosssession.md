---
title: CrossSession | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: b9fcb9c3-7903-478c-9b7c-dbd94092fcba
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 192ddfb7312dff13b457f36940220f0bb17fe2c0
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/02/2019
ms.locfileid: "53909249"
---
# <a name="crosssession"></a>CrossSession
A opção *VSPerfCmd.exe* **CrossSession** permite que o criador de perfil colete dados de qualquer sessão de console. A opção **CrossSession** deve ser usada com a opção **Iniciar**.  
  
 Você pode usar a abreviação **CS** no lugar de **CrossSession**.  
  
## <a name="syntax"></a>Sintaxe  
  
```cmd  
VSPerfCmd.exe /Start:Method /CrossSession [Options]  
```  
  
#### <a name="parameters"></a>Parâmetros  
 Nenhum  
  
## <a name="valid-options"></a>Opções válidas  
 Para habilitar a criação de perfil em outra sessão, a opção **CrossSession** deve ser especificada com a opção **Iniciar**. **CrossSession** também deve ser especificado em qualquer comando **Anexar do VSPerfCmd** e **Desanexar** subsequente.  
  
 **Iniciar:** `Method`  
 A opção **Iniciar** inicializa o criador de perfil para o método de criação de perfil especificado.  
  
 **Anexar:** _PID_[**,**_PID_]  
 Inicia a criação de perfil dos processos especificados.  
  
 **Desanexar**[**:**_PID_[,_PID_]]  
 Para a criação de perfil dos processos especificados.  
  
## <a name="example"></a>Exemplo  
 Neste exemplo, a opção **CrossSession** é usada para anexar a um aplicativo que foi iniciado em outra sessão de console.  
  
```cmd  
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp /CrossSession  
VSPerfCmd.exe /Attach:12345 /CS  
```  
  
## <a name="see-also"></a>Consulte também  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [Criar perfil de aplicativos autônomos](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Criar o perfil de aplicativos Web ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Profile services (Serviços de perfil)](../profiling/command-line-profiling-of-services.md)