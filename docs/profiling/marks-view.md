---
title: Exibição de Marcas | Microsoft Docs
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
ms.workload:
- multiple
ms.openlocfilehash: badb2266e47fcbf0bb20c5fd6fd2f7f25a167997
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62830909"
---
# <a name="marks-view"></a>Exibição de marcas
A exibição Marcas mostra os eventos de amostragem e ETW que foram inseridos no aplicativo.

 As marcas padrão que são pré-populadas no rótulo de relatório no início e no final do programa.

 Dados de contadores do Windows das marcas geradas automaticamente também são apresentadas nesta exibição. Para obter mais informações, confira [Como: Coletar dados de contadores do Windows](../profiling/how-to-collect-windows-counter-data.md).

 Para criar um filtro entre duas marcas, selecione a marca, clique com o botão direito do mouse clique em **Adicionar filtro por marcas** ou **Adicionar filtro por carimbo de data/hora**.

 A tabela a seguir fornece as definições de colunas que estão disponíveis na exibição Marcas.

 **ID de Marca** Identificador exclusivo da marca de criação de perfil.

 **Nome da Marca** O nome do evento.

 **Carimbo de data/hora** Hora de início da criação de perfil até a hora em que o evento é registrado.

 Dados do contador de desempenho do Windows Quando os dados do contador de desempenho do Windows são coletados, os valores são exibidos em uma coluna que tem o nome do contador.

## <a name="see-also"></a>Consulte também
- [Visão geral do relatório de desempenho](../profiling/performance-report-overview.md)
- [Como: Coletar dados de contadores do Windows](../profiling/how-to-collect-windows-counter-data.md)
- [&#91;NIB&#93; janela de controle de coleta de dados](https://msdn.microsoft.com/98d740d8-459f-4605-bf04-fb17aafaaa8f)