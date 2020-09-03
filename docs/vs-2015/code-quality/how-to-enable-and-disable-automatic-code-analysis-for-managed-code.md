---
title: Como habilitar e desabilitar a análise automática de código para código gerenciado | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
ms.assetid: 7c22d194-5fea-4f23-b02d-19344fa64a64
caps.latest.revision: 10
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: d87cc57b31e63ae7aafa53c335df2b56f86a0409
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72658098"
---
# <a name="how-to-enable-and-disable-automatic-code-analysis-for-managed-code"></a>Como habilitar e desabilitar análise de código automática para código gerenciado
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Você pode configurar a análise de código para ser executada antes de cada compilação de um projeto de código gerenciado. Você pode definir diferentes propriedades de análise de código para cada [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] configuração.

### <a name="to-enable-or-disable-automatic-code-analysis"></a>Para habilitar ou desabilitar a análise automática de código

1. Em **Gerenciador de soluções**, clique com o botão direito do mouse no projeto e clique em **Propriedades**.

2. Na caixa de diálogo Propriedades do projeto, clique em **análise de código**.

3. Especifique o tipo de compilação na **configuração** e a plataforma de destino na **plataforma**.

4. Para habilitar ou desabilitar a análise automática de código, marque ou desmarque a caixa de seleção **Habilitar análise de código na compilação (define CODE_ANALYSIS constante)** .
