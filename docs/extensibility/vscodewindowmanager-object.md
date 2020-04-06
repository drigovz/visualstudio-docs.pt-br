---
title: VSCodeWindowManagerObject | Microsoft Docs
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
ms.openlocfilehash: 17bc9462af55ec9621654bd39cd65a2091f3f73f
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80740411"
---
# <a name="vscodewindowmanager-object"></a>Objeto VSCodeWindowManager

O serviço de idiomas implementa o gerenciador de janelas de código e é responsável pelo gerenciamento de adornos (por exemplo, a barra de saque). Para obter mais informações, consulte [Personalizing Code Windows usando a API legado](/visualstudio/extensibility/customizing-code-windows-by-using-the-legacy-api?view=vs-2015).

A tabela a seguir mostra `VSCodeWindowManager` as interfaces no objeto.

|Interface|Descrição|
|---------------|-----------------|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager>|Permite que adornos (como barras paradas) sejam adicionados ou removidos de uma janela de código.|
