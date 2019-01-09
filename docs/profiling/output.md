---
title: Saída | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 5e286e61-4548-42cf-a635-e608c5edbe2b
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 4bca95dea2ac381d28d2c2a4043f94dcfb6fd6e9
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/02/2019
ms.locfileid: "53922242"
---
# <a name="output"></a>Saída
A opção **Saída** especifica o nome do arquivo de dados de criação de perfil para a sessão de desempenho. **Saída** deve ser usado com a opção **Iniciar**.  
  
## <a name="syntax"></a>Sintaxe  
  
```cmd  
VSPerfCmd.exe /Start:Method /Output:FileName [Options]  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `FileName`  
 O nome do arquivo de dados. Caminhos completos e parciais são aceitos. Se um caminho não for especificado, o arquivo será criado no diretório atual.  
  
## <a name="required-options"></a>Opções obrigatórias  
 A opção **Saída** deve ser usada com a opção **Iniciar**.  
  
 **Iniciar:** `Method`  
 Especifica o nome do arquivo de saída.  
  
## <a name="example"></a>Exemplo  
 No exemplo a seguir, o arquivo de dados de criação de perfil é criado no diretório atual.  
  
```cmd  
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp  
```  
  
## <a name="see-also"></a>Consulte também  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [Criar perfil de aplicativos autônomos](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Criar o perfil de aplicativos Web ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Profile services (Serviços de perfil)](../profiling/command-line-profiling-of-services.md)