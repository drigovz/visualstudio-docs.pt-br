---
title: Classe VsgDbg | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 6722263c-ccef-40c7-a0ae-87a863fbab00
caps.latest.revision: 8
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 053647d48324f056148375bae9268b997ba8721f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68145690"
---
# <a name="vsgdbg-class"></a>Classe VsgDbg
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Representa uma interface para o controle programático do componente no aplicativo do diagnóstico de gráficos.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
class VsgDbg;  
```  
  
## <a name="members"></a>Membros  
 A `VsgDbg` classe oferece suporte aos seguintes membros.  
  
### <a name="public-constructors"></a>Construtores públicos  
  
|Name|Descrição|  
|----------|-----------------|  
|[VsgDbg::VsgDbg (Construtor)](../debugger/vsgdbg-vsgdbg-constructor.md)|Constrói uma instância da `VsgDbg` classe e, opcionalmente, prepara o componente no aplicativo do diagnóstico de gráficos para capturar e gravar ativamente informações de gráficos.|  
|[VsgDbg::~VsgDbg (Destruidor)](../debugger/vsgdbg-tilde-vsgdbg-destructor.md)|Destrói uma instância da `VsgDbg` classe.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Name|Descrição|  
|----------|-----------------|  
|[AddMessage](../debugger/addmessage.md)|Adiciona uma mensagem personalizada ao HUD de diagnóstico de gráficos (exibição de cabeçalho).|  
|[BeginCapture](../debugger/begincapture.md)|Inicia um intervalo de captura que terminará com `EndCapture` .|  
|[CaptureCurrentFrame](../debugger/capturecurrentframe.md)|Captura o restante do quadro atual para o arquivo de log de gráficos.|  
|[Copiar (captura programática)](../debugger/copy-programmatic-capture.md)|Copia o conteúdo do arquivo de log de gráficos ativo (. vsglog) em um novo arquivo.|  
|[EndCapture](../debugger/endcapture.md)|Encerra um intervalo de captura que foi iniciado com `BeginCapture` .|  
|[Iniciar](../debugger/init.md)|Prepara o componente no aplicativo de diagnóstico de gráficos para capturar e registrar informações de gráficos ativamente.|  
|[ToggleHUD](../debugger/togglehud.md)|Alterna para ativar ou desativar a sobreposição de HUD de diagnóstico de gráficos.|  
|[UnInit](../debugger/uninit.md)|Finaliza o arquivo de log de gráficos, fecha-o e libera os recursos que foram usados enquanto o aplicativo gravava informações gráficas ativamente.|  
  
## <a name="remarks"></a>Comentários  
 A `VsgDbg` classe representa uma interface que você pode usar para controlar recursos de diagnóstico de gráficos programaticamente. Você pode usar alguns recursos mesmo quando não estiver capturando e gravando ativamente informações de gráficos; Isso inclui a função de `AddMessage` membro e a `ToggleHUD` função de membro. As outras funções de membro preparam o componente no aplicativo do diagnóstico de gráficos para iniciar ou parar a captura ativa de informações de gráficos, ou devem ser chamadas enquanto o aplicativo estiver capturando e gravando informações gráficas em um arquivo de log de gráficos ativamente.
