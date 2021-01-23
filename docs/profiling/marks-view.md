---
title: Exibição de Marcas | Microsoft Docs
description: Saiba como o modo de exibição de marcas exibe eventos de amostragem e ETW que foram inseridos no aplicativo.
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.performance.view.marks
helpviewer_keywords:
- profiling tools, Marks view
- profiling tools reports, Marks view
ms.assetid: b2773344-8081-4116-85a1-58f770448f6a
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 969bf0debfc1da9f7ca1763d8c9c001d565ce64a
ms.sourcegitcommit: 18729d7c99c999865cc2defb17d3d956eb3fe35c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2021
ms.locfileid: "98718974"
---
# <a name="marks-view"></a>Exibição de marcas
A exibição Marcas mostra os eventos de amostragem e ETW que foram inseridos no aplicativo.

 As marcas padrão que são pré-populadas no rótulo de relatório no início e no final do programa.

 Dados de contadores do Windows das marcas geradas automaticamente também são apresentadas nesta exibição. Para obter mais informações, consulte [como: coletar dados do contador do Windows](../profiling/how-to-collect-windows-counter-data.md).

 Para criar um filtro entre duas marcas, selecione a marca, clique com o botão direito do mouse clique em **Adicionar filtro por marcas** ou **Adicionar filtro por carimbo de data/hora**.

 A tabela a seguir fornece as definições de colunas que estão disponíveis na exibição Marcas.

 **ID de Marca** Identificador exclusivo da marca de criação de perfil.

 **Nome da Marca** O nome do evento.

 **Carimbo de data/hora** Hora de início da criação de perfil até a hora em que o evento é registrado.

 Dados do contador de desempenho do Windows Quando os dados do contador de desempenho do Windows são coletados, os valores são exibidos em uma coluna que tem o nome do contador.

## <a name="see-also"></a>Confira também
- [Visão geral do relatório de desempenho](../profiling/performance-report-overview.md)
- [Como: coletar dados do contador do Windows](../profiling/how-to-collect-windows-counter-data.md)
- [ Janela de controle de coleta de dados do&#91;NIB&#93;](/previous-versions/bb385767(v=vs.110))