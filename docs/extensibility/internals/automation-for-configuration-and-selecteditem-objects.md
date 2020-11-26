---
title: Automação para objetos de configuração e SelectedItem | Microsoft Docs
description: Saiba como automatizar a compilação do Visual Studio e os processos de item selecionados usando os objetos Configuration e SelectedItem na interoperabilidade do Shell.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: 5bc4b23662efe688146a7266d1b061d2d9611a45
ms.sourcegitcommit: b1b747063ce0bba63ad2558fa521b823f952ab51
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96190064"
---
# <a name="automation-for-configuration-and-selecteditem-objects"></a>Automação para objetos de configuração e SelectedItem

Você pode automatizar os processos de compilação e item selecionado no Visual Studio.

## <a name="automation-for-builds"></a>Automação para compilações

A compilação ou configuração tem um modelo de automação que é fornecido quando você implementa o <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider> . Para obter mais informações, consulte [Compreender configurações de build](../../ide/understanding-build-configurations.md).

Se você criar um VSPackage e quiser controlar as opções de configuração, deverá usar o modelo de automação.

## <a name="automation-for-selecteditem"></a>Automação para SelectedItem

Você não precisa fornecer uma implementação para o `SelectedItem` objeto porque o Visual Studio contém uma implementação padrão. No entanto, você pode implementar o `SelectedItem` objeto se preferir. Você deve implementar um objeto que contém a `SelectedItem` interface e retornar uma resposta a uma chamada para o <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetPropertyPage%2A> método com `VSITEMID` definido como [__VSHPROPID. VSHPROPID_ExtSelectedItem](<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID.VSHPROPID_ExtSelectedItem>).

## <a name="see-also"></a>Confira também

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetPropertyPage%2A>
- [Contribuir para o modelo de automação](../../extensibility/internals/contributing-to-the-automation-model.md)
- [Noções sobre configurações de build](../../ide/understanding-build-configurations.md)
