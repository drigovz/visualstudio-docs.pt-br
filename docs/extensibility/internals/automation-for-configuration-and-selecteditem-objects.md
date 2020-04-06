---
title: Automação para configuração e objetos selecionados | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- automation [Visual Studio SDK], SelectedItem object
- automation [Visual Studio SDK], builds
ms.assetid: 120377f1-51aa-4445-b2f7-06ab7fc2b47f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 0341cdf56b32b8b1ac77104b3f3e813ae0610767
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80709965"
---
# <a name="automation-for-configuration-and-selecteditem-objects"></a>Automação para configuração e objetos selecionados

Você pode automatizar os processos de compilação e itens selecionados no Visual Studio.

## <a name="automation-for-builds"></a>Automação para construções

A compilação ou configuração tem um <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider>modelo de automação fornecido quando você implementa . Para obter mais informações, consulte [Compreender configurações de build](../../ide/understanding-build-configurations.md).

Se você criar um VSPackage e quiser controlar as opções de configuração, você deve usar o modelo de automação.

## <a name="automation-for-selecteditem"></a>Automação para SelectedItem

Você não precisa fornecer uma `SelectedItem` implementação para o objeto porque o Visual Studio contém uma implementação padrão. No entanto, `SelectedItem` você pode implementar o objeto se preferir. Você deve implementar um `SelectedItem` objeto que contenha a interface <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetPropertyPage%2A> e `VSITEMID` retornar uma resposta a uma chamada para o método com definido para [__VSHPROPID. VSHPROPID_ExtSelectedItem.](<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID.VSHPROPID_ExtSelectedItem>)

## <a name="see-also"></a>Confira também

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetPropertyPage%2A>
- [Contribua para o modelo de automação](../../extensibility/internals/contributing-to-the-automation-model.md)
- [Noções sobre configurações de build](../../ide/understanding-build-configurations.md)
