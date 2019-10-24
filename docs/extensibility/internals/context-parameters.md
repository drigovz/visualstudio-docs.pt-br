---
title: Parâmetros de contexto | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- wizards, context parameters
- context parameters
ms.assetid: 1a062dcb-8a8f-40dd-bea9-3d10f9448966
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9ea38b79be362f78fcc34161a480597fb0ecce40
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72727558"
---
# <a name="context-parameters"></a>Parâmetros de contexto
No [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE (ambiente de desenvolvimento integrado), você pode adicionar assistentes às caixas de diálogo **novo projeto**, **Adicionar novo item**ou **Adicionar subprojeto** . Os assistentes adicionados estão disponíveis no menu **arquivo** ou clicando com o botão direito do mouse em um projeto no **Gerenciador de soluções**. O IDE passa parâmetros de contexto para a implementação do assistente. Os parâmetros de contexto definem o estado do projeto quando o IDE chama o assistente.

 O IDE inicia os assistentes definindo o sinalizador <xref:Microsoft.VisualStudio.Shell.Interop.VSADDITEMOPERATION> na chamada do IDE para o método <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.AddItem%2A> para o projeto. Quando definido, o projeto deve fazer com que o método `IVsExtensibility::RunWizardFile` seja executado usando o nome do assistente registrado ou GUID e outros parâmetros de contexto que o IDE passa para ele.

## <a name="context-parameters-for-new-project"></a>Parâmetros de contexto para novo projeto

| Parâmetro | Descrição |
|-------------------------| - |
| `WizardType` | Tipo de assistente registrado (<xref:EnvDTE.Constants.vsWizardNewProject>) ou o GUID que indica o tipo de assistente. Na implementação de [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)], o GUID do assistente é {0F90E1D0-4999-11D1-B6D1-00A0C90F2744}. |
| `ProjectName` | Uma cadeia de caracteres que é o nome exclusivo do projeto de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. |
| `LocalDirectory` | Local local dos arquivos de projeto de trabalho. |
| `InstallationDirectory` | O caminho do diretório do [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] é instalação. |
| `FExclusive` | Sinalizador booliano que indica que o projeto deve fechar soluções abertas. |
| `SolutionName` | Nome do arquivo de solução sem a parte do diretório ou a extensão *. sln* . O nome do arquivo *. suo* também é criado usando `SolutionName`. Quando esse argumento não é uma cadeia de caracteres vazia, o assistente usa <xref:EnvDTE._Solution.Create%2A> antes de adicionar o projeto com <xref:EnvDTE._Solution.AddFromTemplate%2A>. Se esse nome for uma cadeia de caracteres vazia, use <xref:EnvDTE._Solution.AddFromTemplate%2A> sem chamar <xref:EnvDTE._Solution.Create%2A>. |
| `Silent` | Booliano que indica se o assistente deve ser executado silenciosamente como se o **término** fosse clicado (`TRUE`). |

## <a name="context-parameters-for-add-new-item"></a>Parâmetros de contexto para adicionar novo item

| Parâmetro | Descrição |
|-------------------------| - |
| `WizardType` | Tipo de assistente registrado (<xref:EnvDTE.Constants.vsWizardAddItem>) ou o GUID que indica o tipo de assistente. Na implementação de [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)], o GUID do assistente é {0F90E1D1-4999-11D1-B6D1-00A0C90F2744}. |
| `ProjectName` | Uma cadeia de caracteres que é o nome exclusivo do projeto de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. |
| `ProjectItems` | Localização local que contém arquivos de projeto de trabalho. |
| `ItemName` | Nome do item a ser adicionado. Esse nome é o nome de arquivo padrão ou o nome do arquivo que o usuário digita na caixa de diálogo **Adicionar itens** . O nome é baseado nos sinalizadores que são definidos no arquivo *. vsdir* . O nome pode ser um valor nulo. |
| `InstallationDirectory` | O caminho do diretório do [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] é instalação. |
| `Silent` | Booliano que indica se o assistente deve ser executado silenciosamente como se o **término** fosse clicado (`TRUE`). |

## <a name="context-parameters-for-add-sub-project"></a>Parâmetros de contexto para Add sub Project

| Parâmetro | Descrição |
|-------------------------| - |
| `WizardType` | Tipo de assistente registrado (<xref:EnvDTE.Constants.vsWizardAddSubProject>) ou o GUID que indica o tipo de assistente. Na implementação de [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)], o GUID do assistente é {0F90E1D2-4999-11D1-B6D1-00A0C90F2744}. |
| `ProjectName` | Uma cadeia de caracteres que é o nome exclusivo do projeto de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. |
| `ProjectItems` | Ponteiro para a coleção de `ProjectItems` na qual o assistente Opera. Esse ponteiro é passado para o assistente com base na seleção de hierarquia do projeto. Um usuário normalmente seleciona uma pasta na qual colocar o item e, em seguida, chama a caixa de diálogo **Adicionar item** do projeto. |
| `LocalDirectory` | Local local dos arquivos de projeto de trabalho. |
| `ItemName` | Nome do item a ser adicionado. Esse nome é o nome de arquivo padrão ou o nome do arquivo que o usuário digita na caixa de diálogo **Adicionar itens** . O nome é baseado nos sinalizadores que são definidos no arquivo *. vsdir* . O nome pode ser um valor nulo. |
| `InstallationDirectory` | Caminho do diretório da instalação do [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. |
| `Silent` | Booliano que indica se o assistente deve ser executado silenciosamente como se o **término** fosse clicado (`TRUE`). |

## <a name="see-also"></a>Consulte também
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject2>
- [Parâmetros personalizados](../../extensibility/internals/custom-parameters.md)
- [Assistentes:](../../extensibility/internals/wizards.md)
- [Arquivo do assistente (. vsz)](../../extensibility/internals/wizard-dot-vsz-file.md)
- [Parâmetros de contexto para iniciar assistentes](https://msdn.microsoft.com/Library/051a10f4-9e45-4604-b344-123044f33a24)