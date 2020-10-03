---
title: Suporte ao DirectX 12 no Visual Studio | Microsoft Docs
description: Os usuários do DirectX 12 são recomendados para usar o PIX no Windows para uma experiência de depuração gráfica completa
ms.date: 09/29/2020
ms.topic: conceptual
author: davidcongruili
ms.author: davidli1
manager: mluparu
ms.workload:
- multiple
ms.openlocfilehash: 9dbc52a0233abe467da4d41af0134663bc7cd9df
ms.sourcegitcommit: a1cb4e2025045c2ad79167645c4c0f33b94b1152
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/02/2020
ms.locfileid: "91671393"
---
# <a name="directx-12-support-in-visual-studio"></a>Suporte ao DirectX 12 no Visual Studio

## <a name="directx-12-support"></a>Suporte para DirectX 12

O Visual Studio Diagnóstico de Gráficos não dá suporte a jogos DirectX 12. Para a depuração gráfica com suporte completo para DirectX 12, o Visual Studio recomenda o *PIX no Windows*. 

O PIX no Windows é uma ferramenta de depuração e ajuste de desempenho com recursos remotos. O PIX no Windows oferece sete recursos principais que se adaptam às suas necessidades de depuração gráfica. Depure e analise o desempenho do processamento de gráficos do Direct3D 12 com capturas de GPU. Entenda o desempenho e a Threading de todos os trabalhos de CPU e GPU executados por seu jogo com capturas de tempo. Identifique ineficiências nos padrões de e/s de disco do título e no layout do pacote com capturas de e/s de arquivo.

Pressione em sua jornada de depuração gráfica com o [**PIX no Windows**](https://aka.ms/PIXonWindows).

[**Baixe o PIX no Windows**](https://aka.ms/downloadPIX) ou [ **exiba a documentação**.](https://devblogs.microsoft.com/pix/documentation/)

## <a name="pix-on-windows"></a>PIX no Windows

O PIX no Windows apresenta sete modos principais de operação:
1. A **GPU captura** a depuração e a análise do desempenho da renderização de gráficos do Direct3D 12.
2. **Capturas de tempo** para entender o desempenho e threading de todos os trabalhos de CPU e GPU executados pelo seu jogo e para controlar o uso de memória da GPU.
3. O **Resumo de função captura** informações acumuladas sobre quanto tempo cada função é executada e com que frequência cada uma é chamada.
4. **Capturas de chamadas** rastreiam a execução de uma única função.
5. As **capturas de alocação de memória** fornecem informações sobre as alocações de memória feitas por seu jogo.
6. As **capturas de e/s do arquivo** ajudam a identificar ineficiências nos padrões de e/ou no layout do pacote do seu título.
7. O **Monitor do sistema** exibe dados de contador em tempo real enquanto um jogo está em execução.

Uma introdução de vídeo detalhada para o PIX no Windows está disponível [ **aqui**](https://www.youtube.com/playlist?list=PLeHvwXyqearWuPPxh6T03iwX-McPG5LkB)
