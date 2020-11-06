---
title: Objeto VSCodeWindowManager | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- VSCodeWindowManager
helpviewer_keywords:
- VsCodeWindowManager object
- views [Visual Studio SDK], VSCodeWindowManager object
ms.assetid: e313add5-afdb-4d8d-abd1-764e1fc10c44
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e88885d339e55b7c3df1312b4a72c59d2959bbcc
ms.sourcegitcommit: ba966327498a0f67d2df2291c60b62312f40d1d3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/06/2020
ms.locfileid: "93414339"
---
# <a name="vscodewindowmanager-object"></a>Objeto VSCodeWindowManager

O serviço de linguagem implementa o Gerenciador de janelas de código e é responsável por gerenciar adornos (por exemplo, a barra suspensa). Para obter mais informações, consulte [Personalizando janelas de código usando a API herdada](/previous-versions/visualstudio/visual-studio-2015/extensibility/customizing-code-windows-by-using-the-legacy-api?preserve-view=true&view=vs-2015).

A tabela a seguir mostra as interfaces no `VSCodeWindowManager` objeto.

|Interface|Descrição|
|---------------|-----------------|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager>|Permite que adorners (como barras suspensas) sejam adicionados ou removidos de uma janela de código.|