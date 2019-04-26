---
title: Saída | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 5e286e61-4548-42cf-a635-e608c5edbe2b
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 78d5b39908bc0ffa39533c22ea4effcbe97397b7
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62794211"
---
# <a name="output"></a>Saída
A opção **Saída** especifica o nome do arquivo de dados de criação de perfil para a sessão de desempenho. **Saída** deve ser usado com a opção **Iniciar**.

## <a name="syntax"></a>Sintaxe

```cmd
VSPerfCmd.exe /Start:Method /Output:FileName [Options]
```

#### <a name="parameters"></a>Parâmetros
 `FileName` O nome do arquivo de dados. Caminhos completos e parciais são aceitos. Se um caminho não for especificado, o arquivo será criado no diretório atual.

## <a name="required-options"></a>Opções obrigatórias
 A opção **Saída** deve ser usada com a opção **Iniciar**.

 **Iniciar:** `Method` Especifica o nome do arquivo de saída.

## <a name="example"></a>Exemplo
 No exemplo a seguir, o arquivo de dados de criação de perfil é criado no diretório atual.

```cmd
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp
```

## <a name="see-also"></a>Consulte também
- [VSPerfCmd](../profiling/vsperfcmd.md)
- [Aplicativos Autônomos de Perfil](../profiling/command-line-profiling-of-stand-alone-applications.md)
- [Criar o perfil de aplicativos Web ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)
- [Profile services (Serviços de perfil)](../profiling/command-line-profiling-of-services.md)