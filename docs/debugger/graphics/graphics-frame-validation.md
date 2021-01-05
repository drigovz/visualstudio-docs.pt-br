---
title: Validação de quadro de gráficos | Microsoft Docs
description: Saiba mais sobre a ferramenta de validação de quadro para gráficos no Visual Studio. Essa ferramenta exibe erros e avisos associados à lista de eventos.
ms.custom: SEO-VS-2020
ms.date: 03/02/2017
ms.topic: conceptual
f1_keywords:
- vs.graphics.FrameValidation
ms.assetid: 1e639182-1301-4e28-9c1e-b5df732f3f1b
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0fe9b1ed3acbe588b342ba6550bc45558a2070d2
ms.sourcegitcommit: fcfd0fc7702a47c81832ea97cf721cca5173e930
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2020
ms.locfileid: "97727639"
---
# <a name="graphics-frame-validation"></a>Validação de quadro de gráficos
<!-- VERSIONLESS -->
O Visual Studio 2017 e superior dão suporte à ferramenta de **validação de quadro** .  A janela validação de quadro exibe erros e avisos associados à lista de eventos.  Para exibir essa janela, selecione o menu **Exibir validação de quadro de >** .

![Validação de quadro](media/gfx_diag_frame_validation.png)

Clique no botão **executar validação** no canto superior esquerdo para iniciar a análise.  Pode levar vários minutos para ser concluído, dependendo da complexidade do quadro.  Os dados que aparecem aqui são uma combinação de duas fontes: as mensagens que o próprio D3D emite quando as [camadas do SDK](/windows/desktop/direct3d11/overviews-direct3d-11-devices-layers) estão habilitadas e os dados que são coletados do controle de estado interno da própria ferramenta. Após a conclusão, você verá várias colunas de dados:

| **Coluna** | **Descrição** |
|------------| - |
| ID do evento | ID que mapeia para uma entrada na janela de [lista de eventos](graphics-event-list.md) . |
| Severity | Corrupção, erro, aviso, informações ou mensagem. |
| Categoria | Aplicativo definido, diversos, inicialização, limpeza, compilação, criação de estado, configuração de estado, obtenção de estado, execução, manipulação de recursos, sombreador, redundante e não utilizado. |
| Mensagem | A mensagem associada ao evento. |
| Evento | O evento associado ao erro ou aviso. |

## <a name="see-also"></a>Consulte também
[Diagnóstico de gráficos (depuração de gráficos DirectX)](visual-studio-graphics-diagnostics.md)
<!-- /VERSIONLESS -->