---
title: Subtipos do Projeto | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], subtypes
- project subtypes [Visual Studio SDK]
ms.assetid: d235b47b-cf11-4d47-a63f-e33d9d16105d
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 71dab4767c806b44cbd1f9638738b4a13d6b2bcb
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80706407"
---
# <a name="project-subtypes"></a>Subtipos de projeto
Os subtipos do projeto permitem personalizar ou [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]saborear o comportamento dos sistemas de projeto de . As personalizações incluem a salvação de dados adicionais no arquivo do projeto, a adição ou filtração de itens na caixa de diálogo **Adicionar novo item,** controlar como os conjuntos são depurados e implantados e estender a caixa de diálogo Páginas de **Propriedade** do projeto. VSPackages implementam subtipos de projeto usando agregação COM.

> [!NOTE]
> O sistema de projeto Visual C++ não suporta subtipos de projeto. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]em si, usa subtipos de projeto para implementar projetos de SQL Server e Smart Device.

## <a name="in-this-section"></a>Nesta seção
- [Design de subtipos de projeto](../../extensibility/internals/project-subtypes-design.md)

 Descreve o conceito de subtipos de projetos.

- [Sequência de inicialização de subtipos de projeto](../../extensibility/internals/initialization-sequence-of-project-subtypes.md)

 Descreve a seqüência de inicialização [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] do subtipo do projeto programático por ambiente.

- [Propriedades e métodos estendidos por subtipos de projeto](../../extensibility/internals/properties-and-methods-extended-by-project-subtypes.md)

 Fornece descrições detalhadas dos recursos e métodos mais freqüentemente estendidos usando subtipos de projeto.

- [Mantendo os dados no arquivo de projeto do MSBuild](../../extensibility/internals/persisting-data-in-the-msbuild-project-file.md)

 Descreve como persistir dados em um arquivo <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment> de projeto e como usar para manter os dados no arquivo do projeto através dos níveis de agregação do subtipo do projeto.

- [Interface do usuário de propriedades do projeto](../../extensibility/internals/project-property-user-interface.md)

 Descreve como os subtipos do projeto podem modificar a caixa de diálogo Páginas de **Propriedade** do projeto.

- [Estendendo o modelo de objeto do projeto base](../../extensibility/internals/extending-the-object-model-of-the-base-project.md)

 Fornece informações sobre como os subtipos do projeto podem usar extensores de automação para estender o modelo de objeto de automação.

- [Contribuindo com a caixa de diálogo Adicionar Novo Item](../../extensibility/internals/contributing-to-the-add-new-item-dialog-box.md)

 Descreve como adicionar itens à caixa de diálogo **Adicionar novo item.**

- [Salvar dados em arquivos de projeto](../../extensibility/saving-data-in-project-files.md)

 Explica como um subtipo de projeto pode salvar e recuperar dados específicos do subtipo no arquivo do projeto usando o MPF (Managed Package Framework, framework de pacote gerenciado).

- [Manipulação da implantação especializada](../../extensibility/internals/handling-specialized-deployment.md)

 Explica como os subtipos do projeto podem <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg> fornecer comportamento de implantação especializado implementando a interface.

- [Adicionar e remover páginas de propriedade](../../extensibility/adding-and-removing-property-pages.md)

 Descreve a adição e a remoção de páginas de propriedade no Project Designer.

## <a name="related-sections"></a>Seções relacionadas
- [Tipos de projeto](../../extensibility/internals/project-types.md)

 Fornece links para [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] tópicos detalhando projetos.
