---
title: Inicializar | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: f81bde5c-3394-4b79-a315-c2f6491689b3
caps.latest.revision: 18
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: c910ef1519181f1402cbec1d31686492e30f343d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68154759"
---
# <a name="launch"></a>Inicializar
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

A opção **Inicializar** inicia o criador de perfil usando o método de amostragem e também inicia o aplicativo especificado.  
  
 Para usar a opção **Inicializar**, você deve especificar o método de **Amostragem** na opção **Iniciar**.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
VSPerfCmd.exe /Launch:AppName [Options]  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `AppName`  
 O nome do aplicativo a ser inicializado. Há suporte para caminhos completos e parciais do diretório atual.  
  
## <a name="valid-options"></a>Opções válidas  
 As seguintes opções de VSPerfCmd podem ser combinadas com a opção **Inicializar** em uma única linha de comando.  
  
 **Início:**`Method`  
 Inicializa a sessão de criador de perfil de linha de comando e define o método de criação de perfil especificado.  
  
 **Globalize** e **GlobalOff**  
 Retoma (**GlobalOn**) ou pausa (**GlobalOff**) a criação de perfil, mas não termina a sessão de criação de perfil.  
  
 **Processo:** `PID` e **ProcessOff**:`PID`  
  Retoma (**ProcessOn**) ou pausa (**ProcessOff**) a criação de perfil para o processo especificado.  
  
 **TargetCLR**  
 Especifica a versão do CLR (Common Language Runtime) do .NET Framework a ser analisada quando mais de uma versão for carregada em uma sessão de criação de perfil. Por padrão, a primeira versão carregada é analisada.  
  
## <a name="exclusive-options"></a>Opções Exclusivas  
 As opções a seguir só podem ser usadas com a opção **Inicializar**.  
  
 **Console**  
 Inicia o aplicativo de linha de comando especificado em uma nova janela.  
  
 **Args:**`ArgList`  
 Especifica a lista de argumentos a serem passados para o aplicativo.  
  
 **LineOff**  
 Desabilita a coleta de dados de criação de perfil de nível de linha.  
  
## <a name="sampling-options"></a>Opções de amostragem  
 Uma das seguintes opções de intervalo de amostragem pode ser especificada na linha de comando **Inicializar**. O intervalo de amostragem padrão é 10.000.000 ciclos de relógio do processador.  
  
 **Timer**[**:** `Cycles` ]**PF**[**:** `Events` ]**Sys**[**:** `Events` ]**Counter**[**:** `Name` , `Reload` , `FriendlyName` ]**GC**[:**alocação**&#124;**tempo de vida**]  
 Especifica o número e o tipo do intervalo de amostragem.  
  
- **Temporizador** – exemplifica cada ciclo de relógio do processador `Cycles` não interrompido. Se `Cycles` não for especificado, os 10.000.000 ciclos serão usados.  
  
- **PF** – exemplifica cada `Events` falha de página. Se `Events` não for especificado, 10 falhas de página.  
  
- **Sys** – exemplifica cada `Events` chamadas para o sistema operacional. Se `Events` não for especificado, 10 chamadas do sistema serão usadas.  
  
- **Contador** – exemplifica cada número `Reload` do contador de desempenho de CPU especificado por `Name`. Opcionalmente, `FriendlyName` pode especificar uma cadeia de caracteres para usar como o cabeçalho de coluna nos relatórios do criador de perfil.  
  
- **GC** – Coleta dados da memória de .NET. Por padrão (**alocação**), os dados são coletados em todos os eventos de alocação da memória. Quando o parâmetro de **tempo de vida** é especificado, os dados também são coletados em cada evento de coleta de lixo.  
  
## <a name="example"></a>Exemplo  
 Este exemplo demonstra o uso de **Inicializar** para iniciar um aplicativo.  
  
```  
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp  
VSPerfCmd.exe /Launch:TestApp.exe  
```  
  
## <a name="see-also"></a>Consulte Também  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [Criação de perfil de aplicativos autônomos](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Criação de perfil de aplicativos Web ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Serviços de Criação de Perfil](../profiling/command-line-profiling-of-services.md)
