---
title: Persistência do Projeto | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- persistence, projects
- projects [Visual Studio SDK], persistance
ms.assetid: 42907bcf-4e27-46bd-a8cb-01c2ccd2bde5
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 10a9cde91c0181fbfefbaa353c7c3702f4b36819
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80706453"
---
# <a name="project-persistence"></a>Persistência de projeto
Persistência é uma consideração fundamental do projeto. A maioria dos projetos usa itens de projeto que representam arquivos; [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] também suporta projetos cujos dados não são baseados em arquivos. Tanto os arquivos pertencentes ao projeto quanto ao arquivo do projeto devem ser persistidos. O IDE instrui o projeto a se salvar ou a um item do projeto.

 Modelos para projetos são passados para a fábrica de projetos. Os modelos devem suportar a inicialização de todos os itens do projeto de acordo com as exigências do tipo de projeto específico. Esses modelos podem ser salvos posteriormente como arquivos de projeto e gerenciados pelo IDE através da solução. Para obter mais informações, consulte [Criando instâncias de projeto usando fábricas](../../extensibility/internals/creating-project-instances-by-using-project-factories.md) e [soluções de projetos.](../../extensibility/internals/solutions-overview.md)

 Os itens do projeto podem ser baseados em arquivos ou não baseados em arquivos:

- Os itens baseados em arquivos podem ser locais ou remotos. Em projetos web em C#, por exemplo, as conexões a arquivos em um sistema remoto persistem localmente, enquanto os próprios arquivos persistem no sistema remoto.

- Itens não baseados em arquivos podem salvar itens em um banco de dados ou repositório.

## <a name="commit-models"></a>Comprometer modelos
 Depois de decidir onde os itens do projeto estão localizados, você deve escolher o modelo de compromisso apropriado. Por exemplo, em um modelo baseado em arquivos com arquivos locais, cada projeto pode ser salvo de forma autônoma. Em um modelo de repositório, você pode salvar vários itens em uma transação. Para obter mais informações, consulte [Project Type Design Decisions](../../extensibility/internals/project-type-design-decisions.md).

 Para determinar extensões de nome <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat> de arquivo, os projetos implementam a interface, que fornece informações que permitem ao cliente de um objeto implementar a caixa de diálogo **Salvar como** caixa de diálogo — ou seja, preencher a lista de parada **Salvar como tipo** e gerenciar a extensão inicial do nome do arquivo.

 O IDE `IPersistFileFormat` chama a interface do projeto para indicar que o projeto deve persistir seus itens de projeto conforme apropriado. Portanto, o objeto possui todos os aspectos de seu arquivo e formato. Isso inclui o nome do formato do objeto.

 No caso em que os itens `IPersistFileFormat` não são arquivos, ainda é assim que os itens não baseados em arquivos são persistidos. Arquivos de projeto, como arquivos [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] .vbp para projetos [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] ou arquivos .vcproj para projetos, também devem ser persistidos.

 Para salvar ações, o IDE examina a tabela de documentos em execução <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem> (RDT) e a hierarquia passa os comandos para as <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2> interfaces. O <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem.IsItemDirty%2A> método é implementado para determinar se o item foi modificado. Se o item <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem.SaveItem%2A> tiver, o método é implementado para salvar o item modificado.

 Os métodos `IVsPersistHierarchyItem2` na interface são usados para determinar se um item pode ser recarregado e, se o item pode ser, recarregá-lo. Além disso, <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.IgnoreItemFileChanges%2A> o método pode ser implementado para fazer com que os itens alterados sejam descartados sem serem salvos.

## <a name="see-also"></a>Confira também
- [Lista de verificação: criando novos tipos de projeto](../../extensibility/internals/checklist-creating-new-project-types.md)
- [Criando instâncias de projeto por meio de fábricas de projeto](../../extensibility/internals/creating-project-instances-by-using-project-factories.md)
