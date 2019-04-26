---
title: LineOff | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 76082063-20ef-47ae-ad64-81b43b654865
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b4de8aa278adab0127f3a39d9adcf105f906e152
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62995337"
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

 **Iniciar:** `AppName` Inicia o aplicativo especificado e inicia a criação de perfil com o método de amostragem.

## <a name="example"></a>Exemplo
 Esse exemplo inicia o aplicativo e o criador de perfil e desabilita a amostragem de nível de linha.

```cmd
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp
VSPerfCmd.exe /Launch:TestApp.exe /LineOff
```

## <a name="see-also"></a>Consulte também
- [VSPerfCmd](../profiling/vsperfcmd.md)
- [Aplicativos Autônomos de Perfil](../profiling/command-line-profiling-of-stand-alone-applications.md)
- [Criar o perfil de aplicativos Web ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)
- [Profile services (Serviços de perfil)](../profiling/command-line-profiling-of-services.md)