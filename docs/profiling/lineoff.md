---
title: LineOff | Microsoft Docs
description: Saiba como a opção VSPerfCmd LineOff desabilita a coleta de dados de número de linha quando VSPerfCmd é usado para iniciar o aplicativo.
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 76082063-20ef-47ae-ad64-81b43b654865
author: mikejo5000
ms.author: mikejo
manager: jmartens
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: a141e713dd03f99db6ce47224c64236a0219cdd5
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99917894"
---
# <a name="lineoff"></a>LineOff
Por padrão, o criador de perfil coleta os números de linha do código-fonte e dos dados de deslocamento quando o método de criação de perfil de amostragem estiver sendo usado. A opção **LineOff** do VSPerfCmd desabilita a coleta de dados de número de linha quando o VSPerfCmd é usado para iniciar o aplicativo. Quando o **LineOff** for especificado, os dados de criação de perfil serão coletados para o nível de função.

 É possível usar o **LineOff** somente com a opção de **Inicialização** e quando o criador de perfil tiver sido inicializado para amostragem com a opção **Iniciar**:**Amostra**.

## <a name="syntax"></a>Sintaxe

```cmd
VSPerfCmd.exe /Launch:AppName /LineOff [Options]
```

#### <a name="parameters"></a>Parâmetros
 Nenhum

## <a name="required-options"></a>Opções obrigatórias
 A opção **LineOff** pode ser usada apenas em uma linha de comando que contenha a opção **Inicializar**.

 **Iniciar:** `AppName` Inicia o aplicativo especificado e começa a criação de perfil com o método de amostragem.

## <a name="example"></a>Exemplo
 Esse exemplo inicia o aplicativo e o criador de perfil e desabilita a amostragem de nível de linha.

```cmd
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp
VSPerfCmd.exe /Launch:TestApp.exe /LineOff
```

## <a name="see-also"></a>Confira também
- [VSPerfCmd](../profiling/vsperfcmd.md)
- [Aplicativos Autônomos de Perfil](../profiling/command-line-profiling-of-stand-alone-applications.md)
- [Criar o perfil de aplicativos Web ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)
- [Profile services (Serviços de perfil)](../profiling/command-line-profiling-of-services.md)
