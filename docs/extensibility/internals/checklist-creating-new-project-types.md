---
title: 'Checklist: Criando Novos Tipos de Projetos | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], creating new types
- project types, checklist for creating
ms.assetid: 29eb9c3b-1933-4741-aa85-65a33f0825ba
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 5963083239571af43012e1a79576ee80846d80bd
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80709743"
---
# <a name="checklist-create-new-project-types"></a>Checklist: Crie novos tipos de projetos
Você deve concluir várias tarefas para criar um novo tipo de projeto. A lista de verificação a seguir fornece um guia para essas tarefas:

1. Projete a funcionalidade para o seu novo tipo de projeto. Para obter mais informações, consulte [as decisões de design do tipo Project](../../extensibility/internals/project-type-design-decisions.md).

2. Determine quais editores são usados para código e outros elementos do projeto. Você pode usar os editores principais ou padrão, ou pode criar e usar editores específicos de projeto. Para obter mais informações, consulte [Criar editores e designers personalizados](../../extensibility/creating-custom-editors-and-designers.md) e [como: abrir editores específicos de projetos.](../../extensibility/how-to-open-project-specific-editors.md)

3. Determine o nível de participação que os itens do projeto terão na **Exibição** de Classe e no **Navegador de Objetos**. Para obter mais informações, consulte [As ferramentas de navegação por símbolos de suporte](../../extensibility/internals/supporting-symbol-browsing-tools.md).

4. Obtenha novas classes com base nas decisões de design que você fez anteriormente para o seu projeto e itens de projeto.

5. Escreva o código para os seguintes componentes do tipo de projeto:

    - Fábrica de projetos, para gerenciar a criação de novos projetos e abertura de projetos existentes. Para obter mais informações, consulte [Criar instâncias do projeto usando fábricas de projetos](../../extensibility/internals/creating-project-instances-by-using-project-factories.md).

    - Hierarquia de projeto e manuseio de comando. Para obter mais informações, consulte [Use classes de projeto HierUtil7 para implementar um tipo de projeto (C++)](https://msdn.microsoft.com/library/a5c16a09-94a2-46ef-87b5-35b815e2f346), [Elementos de um modelo de projeto,](../../extensibility/internals/elements-of-a-project-model.md) [componentes do núcleo do modelo do projeto](../../extensibility/internals/project-model-core-components.md)e [MenuCommands vs. OleMenuCommands](/visualstudio/extensibility/menucommands-vs-olemenucommands?view=vs-2015).

    - Gerenciamento de itens do projeto, incluindo a adição do seu projeto à caixa de diálogo **Projeto** Novo. Para obter mais informações, consulte [Adicionar modelos de itens de projeto e projeto](../../extensibility/internals/adding-project-and-project-item-templates.md) e registrar [modelos de projeto e itens](../../extensibility/internals/registering-project-and-item-templates.md).

    - Persistência do estado do projeto e itens individuais. Para obter mais informações, consulte [Abrir e salvar itens do projeto](../../extensibility/internals/opening-and-saving-project-items.md). Para persistência de informações de soluções, consulte [Soluções](../../extensibility/internals/solutions-overview.md).

    - Propriedades independentes de configuração a serem exibidas na janela Propriedades. Para obter mais informações, consulte [Extend properties](../../extensibility/internals/extending-properties.md).

    - Propriedades de configuração do projeto implementadas em páginas de propriedade para mostrar propriedades dependentes da configuração. Para obter mais informações, consulte [Gerenciar opções de configuração](../../extensibility/internals/managing-configuration-options.md).

    - Enumerando saídas para implantação. Para obter mais informações, consulte [a configuração do projeto para saída](../../extensibility/internals/project-configuration-for-output.md).

    - Serviços de startup de projeto. Para obter mais informações, consulte [Elementos de um modelo de projeto](../../extensibility/internals/elements-of-a-project-model.md) e [componentes principais do modelo do projeto](../../extensibility/internals/project-model-core-components.md).

    - Objetos, ou classes `IDispatch`derivadas, disponíveis para automação.

    - Arquivos da tabela de comando XML *(.vsct).* Para obter mais informações, consulte [arquivos da tabela de comando visual Studio (.vsct).](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)

6. Teste, depurar e iniciar seu tipo de projeto.

7. Exibir seu projeto na guia **Projeto** da caixa `VARIANT_TRUE` de diálogo `VSHPROPID_ShowProjInSolutionPage` **Adicionar referência,** definindo como o valor para . Para obter mais informações, consulte <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID> e <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A>.

8. Crie o arquivo Microsoft Installer *(.msi)* para instalar seus VSPackages. Para obter mais informações, consulte [Instalar VSPackages com o Instalador do Windows,](../../extensibility/internals/installing-vspackages-with-windows-installer.md) [Registrar um tipo de projeto](../../extensibility/internals/registering-a-project-type.md)e [VSPackages](../../extensibility/internals/vspackages.md).

## <a name="see-also"></a>Confira também
- [Hierarquias no Visual Studio](../../extensibility/internals/hierarchies-in-visual-studio.md)
- [Quando criar tipos de projetos](../../extensibility/internals/when-to-create-project-types.md)
- [Criar tipos de projeto](../../extensibility/internals/creating-project-types.md)
