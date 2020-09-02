---
title: Iniciar | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: b85d0fe9-f67a-4b7c-8d48-7eecf3f2dfe9
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: df3ccda9730be02bafb7f7d069a26193a4528d1e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "74778265"
---
# <a name="start"></a>Iniciar
A opção **Start** é uma opção *VSPerfCmd.exe* que inicializa o criador de perfil para o método de criação de perfil especificado.

## <a name="syntax"></a>Sintaxe

```cmd
VSPerfCmd.exe /Start:Method /Output:FileName [Options]
```

#### <a name="parameters"></a>Parâmetros
 `Method` Precisa ser uma das seguintes palavras-chave:

- **TRACE** – especifica o método de instrumentação.

- **SAMPLE** – especifica o método de amostragem.

- **COVERAGE** – especifica a cobertura de código.

- **CONCURRENCY** – especifica o método de contenção de recursos.

## <a name="required-options"></a>Opções obrigatórias
 A opção **Output** deverá ser especificada quando **Start** for especificada na linha de comando.

 **Saída:** `filename` Especifica o nome do arquivo de saída.

## <a name="exclusive-options"></a>Opções exclusivas
 As opções a seguir só podem ser usadas com a opção **Start** em uma linha de comando.

 **CrossSession**&#124;**CS** Habilita a criação de perfil entre processos. Há suporte para ambos os nomes de opção **CrossSession** e **CS**.

 **Usuário:**[ `domain\` ] `username` permite que o cliente acesse o monitor da conta especificada.

 **WinCounter:** `Path` [**AutoMark**:`n`] **WinCounter** especifica um contador de desempenho do Windows a ser incluído como uma marca no arquivo de dados de criação de perfil. **AutoMark** especifica o intervalo em milissegundos entre as coletas do arquivo de dados.

## <a name="invalid-options"></a>Opções inválidas
 As opções a seguir não podem ser usadas com a opção **Start** em uma linha de comando.

 **Status O ** **Status** aplica-se aos processos analisados. Ela lista processos e threads e seu estado de perfil atual (Ligado/Desligado). Por exemplo, se um processo for interrompido, **Status** não indicará isso no relatório. **Status** mostrará se perfil do processo foi criado ou não.

 **Shutdown**[**:** `Timeout` ] desativa o criador de perfil.

## <a name="example"></a>Exemplo
 O exemplo a seguir demonstra como usar a opção *VSPerfCmd.exe* **Start** para inicializar o criador de perfil.

```cmd
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp
VSPerfCmd.exe /Launch:TestApp.exe
```

## <a name="see-also"></a>Confira também
- [VSPerfCmd](../profiling/vsperfcmd.md)
- [Aplicativos Autônomos de Perfil](../profiling/command-line-profiling-of-stand-alone-applications.md)
- [Criar o perfil de aplicativos Web ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)
- [Profile services (Serviços de perfil)](../profiling/command-line-profiling-of-services.md)
