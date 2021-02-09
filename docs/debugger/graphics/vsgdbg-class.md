---
title: Classe VsgDbg | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 6722263c-ccef-40c7-a0ae-87a863fbab00
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 67bce62612a85e0bcff5e51cd07d4c374e13b01e
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99861394"
---
# <a name="vsgdbg-class"></a>Classe VsgDbg
Representa uma interface para o controle programático do componente no aplicativo do diagnóstico de gráficos.

## <a name="syntax"></a>Sintaxe

```C++
class VsgDbg;
```

## <a name="members"></a>Membros
 A `VsgDbg` classe oferece suporte aos seguintes membros.

### <a name="public-constructors"></a>Construtores públicos

|Nome|Descrição|
|----------|-----------------|
|[VsgDbg::VsgDbg (Construtor)](vsgdbg-vsgdbg-constructor.md)|Constrói uma instância da `VsgDbg` classe e, opcionalmente, prepara o componente no aplicativo do diagnóstico de gráficos para capturar e gravar ativamente informações de gráficos.|
|[VsgDbg::~VsgDbg (Destruidor)](vsgdbg-tilde-vsgdbg-destructor.md)|Destrói uma instância da `VsgDbg` classe.|

### <a name="public-methods"></a>Métodos públicos

|Nome|Descrição|
|----------|-----------------|
|[AddMessage](addmessage.md)|Adiciona uma mensagem personalizada ao HUD de diagnóstico de gráficos (exibição de cabeçalho).|
|[BeginCapture](begincapture.md)|Inicia um intervalo de captura que terminará com `EndCapture` .|
|[CaptureCurrentFrame](capturecurrentframe.md)|Captura o restante do quadro atual para o arquivo de log de gráficos.|
|[Copiar (captura programática)](copy-programmatic-capture.md)|Copia o conteúdo do arquivo de log de gráficos ativo (. vsglog) em um novo arquivo.|
|[EndCapture](endcapture.md)|Encerra um intervalo de captura que foi iniciado com `BeginCapture` .|
|[Init](init.md)|Prepara o componente no aplicativo de diagnóstico de gráficos para capturar e registrar informações de gráficos ativamente.|
|[ToggleHUD](togglehud.md)|Alterna para ativar ou desativar a sobreposição de HUD de diagnóstico de gráficos.|
|[UnInit](uninit.md)|Finaliza o arquivo de log de gráficos, fecha-o e libera os recursos que foram usados enquanto o aplicativo gravava informações gráficas ativamente.|

## <a name="remarks"></a>Comentários
 A `VsgDbg` classe representa uma interface que você pode usar para controlar recursos de diagnóstico de gráficos programaticamente. Você pode usar alguns recursos mesmo quando não estiver capturando e gravando ativamente informações de gráficos; Isso inclui a função de `AddMessage` membro e a `ToggleHUD` função de membro. As outras funções de membro preparam o componente no aplicativo do diagnóstico de gráficos para iniciar ou parar a captura ativa de informações de gráficos, ou devem ser chamadas enquanto o aplicativo estiver capturando e gravando informações gráficas em um arquivo de log de gráficos ativamente.