---
title: Shell do Visual Studio | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- shell, Visual Studio
- Visual Studio, shell
ms.assetid: cb124ef4-1a6b-4bfe-bfbf-295ef9c07f36
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 60aa48da701857508f9b6fd7fc3d9d0c0603046e
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72722049"
---
# <a name="visual-studio-shell"></a>Shell do Visual Studio
O Shell de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] é o principal agente de integração no [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. O Shell fornece a funcionalidade necessária para permitir que o VSPackages Compartilhe serviços comuns. Como o objetivo da arquitetura da [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] é a principal funcionalidade do VSPackages, o Shell é uma estrutura para fornecer funcionalidade básica e oferecer suporte à comunicação cruzada entre o componente VSPackages.

## <a name="shell-responsibilities"></a>Responsabilidades do Shell
 O Shell tem as seguintes responsabilidades principais:

- Suporte a elementos básicos (por meio de interfaces COM) da interface do usuário. Isso inclui menus e barras de ferramentas padrão, quadros de janelas de documentos ou janelas filhas MDI (interface de vários documentos) e quadros de janelas de ferramentas e suporte a encaixe.

- Manter uma lista em execução de todos os documentos abertos no momento em uma tabela de documentos em execução (RDT) para coordenar a persistência de documentos e garantir que um documento não possa ser aberto em mais de uma maneira, ou em maneiras incompatíveis.

- Dando suporte à interface de roteamento de comandos e manipulação de comandos, `IOleCommandTarget`.

- Carregando VSPackages em momentos apropriados. O carregamento de atraso de um VSPackage é necessário para melhorar o desempenho do Shell.

- Gerenciar determinados serviços compartilhados, como <xref:Microsoft.VisualStudio.Shell.Interop.SVsShell>, que fornece a funcionalidade básica do Shell e <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell>, que fornece a funcionalidade básica de janela.

- Gerenciando os arquivos da solução (. sln). As soluções contêm grupos de projetos relacionados, semelhantes aos arquivos de espaço de trabalho (. C++ DSW) no Visual 6,0.

- Acompanhamento da seleção, do contexto e da moeda em todo o Shell. O Shell acompanha os seguintes tipos de itens:

  - O projeto atual

  - O item de projeto atual ou ItemID a <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> atual

  - A seleção atual para a janela **Propriedades** ou `SelectionContainer`

  - As IDs de contexto da interface do usuário ou CmdUIGuids que controlam a visibilidade de comandos, menus e barras de ferramentas

  - Os elementos atualmente ativos, como a janela ativa, o documento e o Gerenciador de desfazer

  - Os atributos de contexto de usuário que orientam a ajuda dinâmica

  O Shell também Media a comunicação entre o VSPackages instalado e os serviços atuais. Ele dá suporte aos principais recursos do Shell e os torna disponíveis para todos os VSPackages integrados no [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. Esses recursos principais incluem os seguintes itens:

- Caixa de diálogo **sobre** e tela inicial

- **Adicionar novas caixas de diálogo e Adicionar item existente**

- Janela **modo de exibição de classe** e **pesquisador de objetos**

- Caixa de diálogo **referências**

- Janela **estrutura de tópicos do documento**

- Janela de **Ajuda dinâmica**

- **Localizar** e **substituir**

- **Abrir o projeto** e **abrir o arquivo** caixas de diálogo no **novo** menu

- Caixa de diálogo **Opções** no menu **ferramentas**

- Janela **Propriedades**

- **Gerenciador de Soluções**

- Janela de **lista de tarefas**

- **Caixa de Ferramentas**

## <a name="see-also"></a>Consulte também
- <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>
- <xref:Microsoft.VisualStudio.Shell.Interop.SVsShell>
- <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell>
- [VSPackages](../../extensibility/internals/vspackages.md)