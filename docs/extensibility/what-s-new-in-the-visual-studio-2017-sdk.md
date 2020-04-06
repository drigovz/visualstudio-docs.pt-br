---
title: O que&#39;novidades no Visual Studio 2017 SDK | Microsoft Docs
ms.date: 10/31/2017
ms.topic: conceptual
ms.assetid: 9efcf0a3-dbde-4cab-8ed3-425826a48b2e
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 88330aa68f2a3752431fd2fbe6c5c1c649acbb8b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80697202"
---
# <a name="what39s-new-in-the-visual-studio-2017-sdk"></a>O que&#39;novidades no Visual Studio 2017 SDK 2017

O Visual Studio SDK tem os seguintes recursos novos e atualizados para o Visual Studio 2017.

## <a name="vsix-v3-format"></a>Formato VSIX v3

Para suportar a nova instalação leve do Visual Studio 2017, o formato de manifesto de extensão VSIX foi atualizado para a versão 3 (VSIX v3).

O novo formato tem suporte para:

* Declarando explicitamente pré-requisitos a serem detectados e instalados pelo VSIXInstaller.
* Montagens ngen sobre instalação de extensão.
* Instalação de ativos fora da raiz de extensão usual.

Para saber mais sobre essas mudanças, consulte os seguintes tópicos:

* [Mudanças na extensibilidade do Visual Studio 2017](breaking-changes-2017.md)
* [Suporte a NGen no VSIX v3](ngen-support.md)
* [Instalar fora da pasta de extensões](set-install-root.md)
* [Perguntas frequentes para a extensibilidade do Visual Studio 2017](faq-2017.md)

## <a name="migrate-extensibility-project-to-visual-studio-2017"></a>Migrar projeto de extensibilidade para o Visual Studio 2017

Para saber como atualizar seus projetos de extensibilidade e seus manifestos VSIX para o Visual Studio 2017, veja [Como: Migrar projetos de extensibilidade para o Visual Studio 2017](how-to-migrate-extensibility-projects-to-visual-studio-2017.md).

## <a name="custom-project-and-item-templates"></a>Modelos personalizados de projetos e itens

A partir do Visual Studio 2017, a digitalização para modelos personalizados de projetos e itens não será mais realizada. Em vez disso, a extensão deve fornecer arquivos manifestos de modelo que descrevem a localização de instalação desses modelos. Você pode usar o Visual Studio 2017 para atualizar suas extensões VSIX. Se você implantar sua extensão usando um MSI, você deve gerar os arquivos manifestos de modelo manualmente. Para obter mais informações, consulte [Atualizar modelos personalizados de projeto e itens para o Visual Studio 2017](../extensibility/upgrading-custom-project-and-item-templates-for-visual-studio-2017.md). O esquema de manifesto de modelo está documentado no [modelo visual studio manifesta referência de esquema](../extensibility/visual-studio-template-manifest-schema-reference.md).

## <a name="updated-extension-performance-guidelines"></a>Diretrizes atualizadas de desempenho de extensão

Há um novo [artigo Como: Diagnosticar](how-to-diagnose-extension-performance.md) o desempenho de extensão em Manage [VSPackages](managing-vspackages.md) para mostrar como detectar e analisar o impacto da extensão na inicialização do Visual Studio e nos tempos de carga da solução.
