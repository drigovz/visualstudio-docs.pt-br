---
title: Classe VsgDbg | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 6722263c-ccef-40c7-a0ae-87a863fbab00
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 4051a02de6a046621e62c21b4d2399b5a2703cb8
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62895186"
---
# <a name="vsgdbg-class"></a>Classe VsgDbg
Representa uma interface para o controle programático do componente no aplicativo do diagnóstico de gráficos.

## <a name="syntax"></a>Sintaxe

```C++
class VsgDbg;
```

## <a name="members"></a>Membros
 O `VsgDbg` classe oferece suporte aos seguintes membros.

### <a name="public-constructors"></a>Construtores públicos

|Nome|Descrição|
|----------|-----------------|
|[VsgDbg::VsgDbg (Construtor)](vsgdbg-vsgdbg-constructor.md)|Constrói uma instância do `VsgDbg` de classe e, opcionalmente, prepara o componente no aplicativo de diagnóstico de gráficos para capturar ativamente e registrar informações de gráficos.|
|[VsgDbg::~VsgDbg (Destruidor)](vsgdbg-tilde-vsgdbg-destructor.md)|Destrói uma instância da `VsgDbg` classe.|

### <a name="public-methods"></a>Métodos públicos

|Nome|Descrição|
|----------|-----------------|
|[AddMessage](addmessage.md)|Adiciona uma mensagem personalizada para o diagnóstico de gráficos HUD (Head-Up Display).|
|[BeginCapture](begincapture.md)|Inicia um intervalo de captura que terminará com `EndCapture`.|
|[CaptureCurrentFrame](capturecurrentframe.md)|Captura o restante do quadro atual para o arquivo de log de gráficos.|
|[Copiar (captura programática)](copy-programmatic-capture.md)|Copia o conteúdo do arquivo de log (. vsglog) de elementos gráficos ativos em um novo arquivo.|
|[EndCapture](endcapture.md)|Termina um intervalo de captura foi iniciado com `BeginCapture`.|
|[Init](init.md)|Prepara o componente no aplicativo de diagnóstico de gráficos para capturar ativamente e registrar informações de gráficos.|
|[ToggleHUD](togglehud.md)|Alterna a sobreposição HUD do diagnóstico de gráficos ativada ou desativada.|
|[UnInit](uninit.md)|Finaliza o arquivo de log de gráficos, fecha e libera os recursos que foram usados enquanto o aplicativo ativamente estava gravando informações de gráficos.|

## <a name="remarks"></a>Comentários
 O `VsgDbg` classe representa uma interface que você pode usar para controlar recursos de diagnóstico de gráficos programaticamente. Você pode usar alguns recursos mesmo quando você estiver ativamente capturar e registrar informações de gráficos; Isso inclui o `AddMessage` função de membro e `ToggleHUD` função de membro. As outras funções de membro ou preparar o componente no aplicativo de diagnóstico de gráficos para iniciar ou parar a captura de ativa de informações de gráficos ou devem ser chamadas enquanto o aplicativo está ativamente capturando e gravar informações de gráficos em um arquivo de log de gráficos.