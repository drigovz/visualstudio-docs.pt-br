---
title: Usuário (VSPerfCmd) | Microsoft Docs
description: Saiba como a opção usuário especifica o domínio e o nome de usuário da conta que possui o processo de perfil.
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: ee1a478e-374d-4f30-ae28-d260b9d4723a
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: dbb5490ff9281a7379d74209da15a3a39595bc09
ms.sourcegitcommit: 18729d7c99c999865cc2defb17d3d956eb3fe35c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2021
ms.locfileid: "98721154"
---
# <a name="user-vsperfcmd"></a>Usuário (VSPerfCmd)
A opção **Usuário** especifica o domínio e o nome de usuário da conta que possui o processo com perfil. Esta opção é necessária apenas se o processo estiver sendo executado como um usuário diferente do usuário conectado. O proprietário do processo é listado na coluna Nome de Usuário na guia **Processos** do Gerenciador de Tarefas do Windows.

 A opção **Usuário** só pode ser especificada em uma linha de comando que também contém a opção **Iniciar**.

## <a name="syntax"></a>Sintaxe

```cmd
VSPerfCmd.exe /Start:Method /Output:FileName /User:[Domain\]UserName [Options]
```

#### <a name="parameters"></a>Parâmetros
 `Domain` O nome do domínio do usuário.

 `UserName` O nome do usuário.

## <a name="required-options"></a>Opções obrigatórias
 A opção **Usuário** só pode ser usada com a opção **Iniciar**.

 **Início:** `Method` Inicializa o criador de perfil para o método de criação de perfil especificado.

## <a name="example"></a>Exemplo
 O exemplo a seguir demonstra o uso da opção **Usuário**.

```cmd
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp /User:SYSTEM
```

## <a name="see-also"></a>Confira também
- [VSPerfCmd](../profiling/vsperfcmd.md)
- [Aplicativos Autônomos de Perfil](../profiling/command-line-profiling-of-stand-alone-applications.md)
- [Criar o perfil de aplicativos Web ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)
- [Profile services (Serviços de perfil)](../profiling/command-line-profiling-of-services.md)
