---
title: Parâmetros de contexto | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- wizards, context parameters
- context parameters
ms.assetid: 1a062dcb-8a8f-40dd-bea9-3d10f9448966
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6673ad8f26c94165635b5f1bc652b91dcbbfd24f
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80709303"
---
# <a name="context-parameters"></a>Parâmetros de contexto
No [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ambiente de desenvolvimento integrado (IDE), você pode adicionar assistentes ao **Novo Projeto,** **Adicionar novo item**ou adicionar caixas de diálogo **do Projeto Sub.** Os assistentes adicionados estão disponíveis no menu **Arquivo** ou clicando com o botão direito do mouse em um projeto no **Solution Explorer**. O IDE passa parâmetros de contexto para a implementação do assistente. Os parâmetros de contexto definem o estado do projeto quando o IDE chama o assistente.

 O IDE inicia os <xref:Microsoft.VisualStudio.Shell.Interop.VSADDITEMOPERATION> assistentes definindo a bandeira na <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.AddItem%2A> chamada do IDE para o método para o projeto. Quando definido, o projeto `IVsExtensibility::RunWizardFile` deve fazer com que o método seja executado usando o nome do assistente registrado ou GUID e outros parâmetros de contexto que o IDE passa para ele.

## <a name="context-parameters-for-new-project"></a>Parâmetros de contexto para novo projeto

| Parâmetro | Descrição |
|-------------------------| - |
| `WizardType` | Tipo de assistente<xref:EnvDTE.Constants.vsWizardNewProject>registrado ( ) ou o GUID que indica o tipo de assistente. Na [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] implementação, o GUID para o assistente é {0F90E1D0-4999-11D1-B6D1-00A0C90F2744}. |
| `ProjectName` | Uma string que [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] é o nome único do projeto. |
| `LocalDirectory` | Localização local de arquivos de projeto de trabalho. |
| `InstallationDirectory` | O caminho do [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] diretório do é a instalação. |
| `FExclusive` | Bandeira booleana que indica que o projeto deve fechar soluções abertas. |
| `SolutionName` | Nome do arquivo de solução sem a parte do diretório ou a extensão *.sln.* O nome do arquivo *.suo* `SolutionName`também é criado usando . Quando este argumento não é uma <xref:EnvDTE._Solution.Create%2A> seqüência de <xref:EnvDTE._Solution.AddFromTemplate%2A>string vazia, o assistente usa antes de adicionar o projeto com . Se este nome for uma <xref:EnvDTE._Solution.AddFromTemplate%2A> seqüência de string vazia, use sem chamar <xref:EnvDTE._Solution.Create%2A>. |
| `Silent` | Booleano que indica se o assistente deve correr`TRUE`silenciosamente como se o **acabamento** fosse clicado (). |

## <a name="context-parameters-for-add-new-item"></a>Parâmetros de contexto para adicionar novo item

| Parâmetro | Descrição |
|-------------------------| - |
| `WizardType` | Tipo de assistente<xref:EnvDTE.Constants.vsWizardAddItem>registrado ( ) ou o GUID que indica o tipo de assistente. Na [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] implementação, o GUID para o assistente é {0F90E1D1-4999-11D1-B6D1-00A0C90F2744}. |
| `ProjectName` | Uma string que [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] é o nome único do projeto. |
| `ProjectItems` | Localização local que contém arquivos de projeto de trabalho. |
| `ItemName` | Nome do item a ser adicionado. Este nome é o nome do arquivo padrão ou o nome do arquivo que o usuário digita na caixa de diálogo **Adicionar itens.** O nome é baseado nas bandeiras definidas no arquivo *.vsdir.* O nome pode ser um valor nulo. |
| `InstallationDirectory` | O caminho do [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] diretório do é a instalação. |
| `Silent` | Booleano que indica se o assistente deve correr`TRUE`silenciosamente como se o **acabamento** fosse clicado (). |

## <a name="context-parameters-for-add-sub-project"></a>Parâmetros de contexto para adicionar sub projeto

| Parâmetro | Descrição |
|-------------------------| - |
| `WizardType` | Tipo de assistente<xref:EnvDTE.Constants.vsWizardAddSubProject>registrado ( ) ou o GUID que indica o tipo de assistente. Na [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] implementação, o GUID para o assistente é {0F90E1D2-4999-11D1-B6D1-00A0C90F2744}. |
| `ProjectName` | Uma string que [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] é o nome único do projeto. |
| `ProjectItems` | Ponteiro para `ProjectItems` a coleção na qual o assistente opera. Este ponteiro é passado para o assistente com base na seleção de hierarquia do projeto. Um usuário normalmente seleciona uma pasta na qual colocar o item e, em seguida, chama a caixa de diálogo **Adicionar item** do projeto. |
| `LocalDirectory` | Localização local de arquivos de projeto de trabalho. |
| `ItemName` | Nome do item a ser adicionado. Este nome é o nome do arquivo padrão ou o nome do arquivo que o usuário digita na caixa de diálogo **Adicionar itens.** O nome é baseado nas bandeiras definidas no arquivo *.vsdir.* O nome pode ser um valor nulo. |
| `InstallationDirectory` | Caminho do diretório [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] da instalação. |
| `Silent` | Booleano que indica se o assistente deve correr`TRUE`silenciosamente como se o **acabamento** fosse clicado (). |

## <a name="see-also"></a>Confira também
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject2>
- [Parâmetros personalizados](../../extensibility/internals/custom-parameters.md)
- [Assistentes](../../extensibility/internals/wizards.md)
- [Arquivo Assistente (.vsz)](../../extensibility/internals/wizard-dot-vsz-file.md)
- [Parâmetros de contexto para o lançamento de assistentes](https://msdn.microsoft.com/Library/051a10f4-9e45-4604-b344-123044f33a24)
