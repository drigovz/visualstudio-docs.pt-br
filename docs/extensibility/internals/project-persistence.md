---
title: Persistência do projeto | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- persistence, projects
- projects [Visual Studio SDK], persistance
ms.assetid: 42907bcf-4e27-46bd-a8cb-01c2ccd2bde5
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a95c919de9b87ed1782cbdcb029efbf191958f5a
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72725458"
---
# <a name="project-persistence"></a>Persistência de projeto
A persistência é uma consideração de design importante para seu projeto. A maioria dos projetos usa itens de projeto que representam arquivos;  o [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] também dá suporte a projetos cujos dados não são baseados em arquivo. Os arquivos pertencentes ao projeto e ao arquivo de projeto devem ser persistidos. O IDE instrui o projeto a salvar a si mesmo ou um item de projeto.

 Os modelos para projetos são passados para a fábrica de projetos. Os modelos devem dar suporte à inicialização de todos os itens de projeto de acordo com os requisitos do tipo de projeto específico. Esses modelos podem ser salvos posteriormente como arquivos de projeto e gerenciados pelo IDE por meio da solução. Para obter mais informações, consulte [criando instâncias de projeto usando fábricas](../../extensibility/internals/creating-project-instances-by-using-project-factories.md) e [soluções](../../extensibility/internals/solutions-overview.md)de projeto.

 Os itens de projeto podem ser baseados em arquivo ou não baseados em arquivo:

- Os itens baseados em arquivo podem ser locais ou remotos. Em projetos da Web C#no, por exemplo, as conexões com arquivos em um sistema remoto persistem localmente, enquanto os próprios arquivos persistem no sistema remoto.

- Itens não baseados em arquivo podem salvar itens em um banco de dados ou repositório.

## <a name="commit-models"></a>Confirmar modelos
 Depois de decidir onde os itens de projeto estão localizados, você deve escolher o modelo de confirmação apropriado. Por exemplo, em um modelo baseado em arquivo com arquivos locais, cada projeto pode ser salvo de forma autônoma. Em um modelo de repositório, você pode salvar vários itens em uma transação. Para obter mais informações, consulte [Project Type design decisions](../../extensibility/internals/project-type-design-decisions.md).

 Para determinar as extensões de nome de arquivo, os projetos implementam a interface <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat>, que fornece informações que permitem que o cliente de um objeto implemente a caixa de diálogo **salvar como** — ou seja, preencha a lista suspensa **salvar como tipo** e gerencie o extensão de nome de arquivo inicial.

 O IDE chama a interface `IPersistFileFormat` no projeto para indicar que o projeto deve manter seus itens de projeto conforme apropriado. Portanto, o objeto possui todos os aspectos de seu arquivo e formato. Isso inclui o nome do formato do objeto.

 No caso em que os itens não são arquivos, `IPersistFileFormat` ainda é como os itens não baseados em arquivo são persistidos. Arquivos de projeto, como arquivos. vbp para projetos [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] ou arquivos. vcproj para projetos [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)], também devem ser persistidos.

 Para salvar ações, o IDE examina a tabela de documentos em execução (RDT) e a hierarquia passa os comandos para as interfaces <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem> e <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2>. O método <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem.IsItemDirty%2A> é implementado para determinar se o item foi modificado. Se o item tiver, o método <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem.SaveItem%2A> será implementado para salvar o item modificado.

 Os métodos na interface `IVsPersistHierarchyItem2` são usados para determinar se um item pode ser recarregado e, se o item puder ser, recarregá-lo. Além disso, o método <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.IgnoreItemFileChanges%2A> pode ser implementado para fazer com que os itens alterados sejam descartados sem serem salvos.

## <a name="see-also"></a>Consulte também
- [Lista de verificação: criar novos tipos de projeto](../../extensibility/internals/checklist-creating-new-project-types.md)
- [Criar instâncias de projetos usando fábricas de projetos](../../extensibility/internals/creating-project-instances-by-using-project-factories.md)