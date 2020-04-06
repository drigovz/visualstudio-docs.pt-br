---
title: Criando um Plug-in de controle de origem | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- plug-ins, source control
- source control plug-ins
- source control [Visual Studio SDK], plug-ins
ms.assetid: c7e69fa4-150e-469a-a6fc-fa1260bdbb07
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9e0d9dc54a61cabe7bdd5c21c10abf0def34ff6a
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80709182"
---
# <a name="create-a-source-control-plug-in"></a>Criar um plug-in de controle de origem
O Visual Studio SDK fornece recursos que permitem [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] adicionar capacidade de controle de origem ao ambiente de desenvolvimento integrado (IDE). Ele permite que você use qualquer DLL plug-in que esteja em conformidade com a API plug-in de controle de origem descrita nesta documentação.

## <a name="in-this-section"></a>Nesta seção
- [Introdução](../../extensibility/internals/getting-started-with-source-control-plug-ins.md)

 Descreve como instalar um plug-in de controle de origem e destaca as versões atualmente disponíveis da API de controle de fonte.

- [Arquitetura](../../extensibility/internals/source-control-plug-in-architecture.md)

 Usa um diagrama de arquitetura para explicar a [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] integração de um plug-in de controle de origem com o IDE.

- [Guia de teste](../../extensibility/internals/test-guide-for-source-control-plug-ins.md)

 Fornece orientações sobre como testar a instalação e o funcionamento de um plug-in de controle de origem.

## <a name="related-sections"></a>Seções relacionadas
- [Crie um controle de origem VSPackage](../../extensibility/internals/creating-a-source-control-vspackage.md)

 Discute como criar um controle de origem VSPackage que não apenas [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] fornece a funcionalidade de controle de origem, mas substitui a interface do ui de controle de origem.

- [Plug-ins de controle de origem](../../extensibility/source-control-plug-ins.md)

 Fornece uma lista completa de todos os elementos da API plug-in de controle de fonte.

- [Controle de origem](../../extensibility/internals/source-control.md)

 Discute as opções para implementar o controle [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]de origem como uma característica integrada de .
