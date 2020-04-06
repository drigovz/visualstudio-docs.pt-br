---
title: Visual Studio Shell | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- shell, Visual Studio
- Visual Studio, shell
ms.assetid: cb124ef4-1a6b-4bfe-bfbf-295ef9c07f36
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: fb89fc3b82dc7f142714608d8a669e368216c729
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80703997"
---
# <a name="visual-studio-shell"></a>Shell do Visual Studio
O [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] projétil é o [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]principal agente de integração em . O shell fornece funcionalidade necessária para permitir que os VSPackages compartilhem serviços comuns. Como o objetivo [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] arquitetônico é colete a funcionalidade primária nos VSPackages, o shell é uma estrutura para fornecer funcionalidade básica e suporte à comunicação cruzada entre seus vsPackages componentes.

## <a name="shell-responsibilities"></a>Responsabilidades shell
 O shell tem as seguintes responsabilidades principais:

- Suporte (através de interfaces COM) elementos básicos da interface do usuário (Interface do Usuário). Estes incluem menus e barras de ferramentas padrão, quadros de janelas de documentos ou janelas de crianças de interface de vários documentos (MDI) e quadros de janelas de ferramentas e suporte de encaixe.

- Manter uma lista em execução de todos os documentos atualmente abertos em uma tabela de documentos em execução (RDT) a fim de coordenar a persistência dos documentos e garantir que um documento não pode ser aberto de uma maneira, ou de maneira incompatível.

- Suportando a interface de roteamento `IOleCommandTarget`de comando e manuseio de comandos, .

- Carregando VSPacotes em horários apropriados. O atraso no carregamento de um VSPackage é necessário para melhorar o desempenho do shell.

- Gerenciamento de certos serviços <xref:Microsoft.VisualStudio.Shell.Interop.SVsShell>compartilhados, como, como <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell>, que fornece funcionalidade básica shell, e , que fornece funcionalidade básica de janelas.

- Gerenciamento dos arquivos de solução (.sln). As soluções contêm grupos de projetos relacionados, semelhantes aos arquivos de espaço de trabalho (.dsw) no Visual C++ 6.0.

- Rastreando a seleção, o contexto e a moeda em todo o shell. O shell rastreia os seguintes tipos de itens:

  - O projeto atual

  - O item atual do projeto ou ItemID da corrente<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>

  - A seleção atual para a janela **Propriedades** ou`SelectionContainer`

  - Os IDs de contexto de Interface do Usuário ou CmdUIGuids que controlam a visibilidade de comandos, menus e barras de ferramentas

  - Os elementos ativos atualmente, como a janela ativa, documento e desfazer o gerenciador

  - Os atributos de contexto do usuário que impulsionam a Ajuda Dinâmica

  O shell também media a comunicação entre VSPackages instalados e serviços atuais. Ele suporta os recursos principais da shell e os disponibiliza para todos os VSPackages integrados em [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. Esses recursos principais incluem os seguintes itens:

- **Sobre** caixa de diálogo e tela de respingo

- Adicionar caixas de diálogo **de itens novos e adicionais existentes**

- **Janela de exibição de** classe e **navegador de objetos**

- Caixa de diálogo **de referências**

- **Janela de contorno de documento**

- **Janela de ajuda dinâmica**

- **Encontrar** e **Substituir**

- **Abrir as** caixas de diálogo Projeto e **Arquivo Aberto** no menu **Novo**

- Caixa de diálogo **de opções** no menu **Ferramentas**

- **Janela de propriedades**

- **Gerenciador de Soluções**

- **Janela lista de** tarefas

- **Caixa de Ferramentas**

## <a name="see-also"></a>Confira também
- <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>
- <xref:Microsoft.VisualStudio.Shell.Interop.SVsShell>
- <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell>
- [VSPackages](../../extensibility/internals/vspackages.md)
