---
title: Fornecendo automação para VSPackages | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSPackages, automation [Visual Studio SDK]
- automation [Visual Studio SDK], VSPackages
ms.assetid: 104c4c55-78b8-42f4-b6b0-9a334101aaea
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6364f9cbaf3409e076eeb77365e5d793c7be96cb
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80705956"
---
# <a name="providing-automation-for-vspackages"></a>Fornecendo automação para VSPackages
Existem duas maneiras principais de fornecer automação para seus VSPackages: implementando objetos específicos do VSPackage e implementando objetos de automação padrão. Geralmente, estes são usados em conjunto para ampliar o modelo de automação do ambiente.

## <a name="vspackage-specific-objects"></a>VsObjetos específicos de pacote
 Certos lugares dentro do modelo de automação exigem que você forneça objetos de automação exclusivos do seu VSPackage. Por exemplo, novos projetos exigem objetos distintos que apenas o VSPackage fornece. Os nomes desses objetos são inseridos no registro `DTE` e obtidos através de chamadas para o objeto do ambiente.

 Objetos específicos do VSPackage também podem ser obtidos quando um consumidor de automação usa o objeto fornecido através da propriedade Object de um objeto padrão. Por exemplo, `Window` o objeto `Object` padrão tem uma `Windows.Object` propriedade, comumente conhecida como propriedade. Quando os `Window.Object` consumidores chamam a janela em uma janela implementada em seu VSPackage, você repassa um objeto de automação específico do seu próprio design.

#### <a name="projects"></a>Projetos
 O VSPackages pode estender o modelo de automação para novos tipos de projeto através de seus próprios objetos específicos do VSPackage. O objetivo principal de fornecer novos objetos de automação para <xref:Microsoft.VisualStudio.VCProjectEngine.VCProject> o <xref:VSLangProj80.VSProject2> seu VSPackage é diferenciar seus objetos de projeto exclusivos de um ou de um objeto. Essa diferenciação é útil quando você quer fornecer uma maneira de destacar ou iterar seu tipo de projeto além de outros tipos de projeto, caso eles apareçam lado a lado em uma solução. Para obter mais informações, consulte [Expondo Objetos do Projeto](../../extensibility/internals/exposing-project-objects.md).

#### <a name="events"></a>Eventos
 A arquitetura de eventos do ambiente oferece outro lugar para você anexar seus próprios objetos específicos do VSPackage. Por exemplo, criando seus próprios objetos de eventos exclusivos, você pode estender o modelo de eventos do ambiente para projetos. Você pode querer fornecer seus próprios eventos quando um novo item é adicionado ao seu próprio tipo de projeto. Para obter mais informações, consulte [Expondo Eventos](../../extensibility/internals/exposing-events-in-the-visual-studio-sdk.md).

#### <a name="window-objects"></a>Objetos de janela
 O Windows pode repassar um objeto de automação específico do VSPackage de volta ao ambiente quando chamado. Você implementa um objeto <xref:Microsoft.VisualStudio.Shell.Interop.IVsExtensibleObject>derivado <xref:EnvDTE.IExtensibleObject> `IDispatch` de , ou que devolve propriedades, estendendo o objeto de janela no qual ele está situado. Por exemplo, você pode usar essa abordagem para fornecer automação para um controle situado em um quadro de janela. A semântica deste objeto e de qualquer outro objeto que ele possa estender são seus para projetar. Para obter mais informações, consulte [Como: Fornecer automação para Windows](../../extensibility/internals/how-to-provide-automation-for-windows.md).

#### <a name="options-pages-on-the-tools-menu"></a>Páginas de opções no menu Ferramentas
 Você pode criar páginas para estender o modelo de automação de ferramentas, opções através da implementação de páginas e da adição de informações ao registro para criar suas próprias opções. Suas páginas podem então ser chamadas através do modelo de objeto ambiente como qualquer outra página de opções. Se o design do recurso que você está adicionando ao ambiente através do VSPackages requer páginas de opções, então você deve adicionar o suporte à automação também. Para obter mais informações, consulte [Suporte de automação para páginas de opções](../../extensibility/internals/automation-support-for-options-pages.md).

## <a name="standard-automation-objects"></a>Objetos de automação padrão
 Para ampliar a automação para projetos, você também `IDispatch`implementa objetos de automação padrão (derivados) que ficam ao lado dos outros objetos do projeto e implementam métodos e propriedades padrão. Exemplos de objetos padrão incluem os objetos do projeto `Projects`inseridos `ProjectItem`na `ProjectItems`hierarquia da solução, tais como, `Project`e . Cada novo tipo de projeto deve implementar esses objetos (e possivelmente outros, dependendo da semântica do seu projeto).

 De certa forma, esses objetos fornecem a vantagem oposta dos objetos de projeto específicos do VSPackage. Os objetos de automação padrão permitem que seu projeto seja usado de forma generalizada como qualquer outro projeto que suporte os mesmos objetos. Assim, um complemento que é `Project` `ProjectItem` escrito contra o geral e objetos pode funcionar contra projetos de qualquer tipo. Para obter mais informações, consulte [Modelagem de projetos](../../extensibility/internals/project-modeling.md).
