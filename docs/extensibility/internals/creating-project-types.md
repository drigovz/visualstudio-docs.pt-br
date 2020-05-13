---
title: Criando tipos de projetos | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- project types, new
- projects [Visual Studio SDK], new project types
ms.assetid: bdb2d22e-d622-450c-bb2d-98152a745fcf
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d2398b63b8cd52784252cfc764bb6c6a30e1accc
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80709075"
---
# <a name="create-project-types"></a>Criar tipos de projeto
Você pode [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] estender criando um novo tipo de projeto. Para criar um novo tipo de projeto, você deve entender vários conceitos e completar uma série de etapas. Os tópicos a seguir fornecem uma visão geral de como criar tipos de projetos.

## <a name="in-this-section"></a>Nesta seção
- [Decisões de projeto de design](../../extensibility/internals/project-type-design-decisions.md)

 Discute o item, a persistência do arquivo de projeto e as decisões de design mecânico de compromisso que você tem que tomar antes de criar um novo tipo de projeto.

- [Checklist: Crie novos tipos de projetos](../../extensibility/internals/checklist-creating-new-project-types.md)

 Fornece uma visão geral das etapas que você deve seguir para criar um novo tipo de projeto que suporte tarefas de programação como edição de código e compilação, construção, depuração e implantação de aplicativos em seu projeto.

- [Criar instâncias de projeto usando fábricas de projetos](../../extensibility/internals/creating-project-instances-by-using-project-factories.md)

 Fornece informações sobre como fornecer e usar uma fábrica de projetos para criar instâncias de um novo projeto.

- [Registre um tipo de projeto](../../extensibility/internals/registering-a-project-type.md)

 Fornece amostras de código de declarações do registro que fornecem caminhos e dados padrão, e uma tabela que contém entradas do script de registro para cada declaração.

- [Persistência do projeto](../../extensibility/internals/project-persistence.md)

 Discute o uso `IPersistFileFormat` de para persistir tanto objetos de projeto baseados em arquivos quanto não baseados em arquivos.

- [Use MSBuild](../../extensibility/internals/using-msbuild.md)

 Descreve como seu tipo de [!INCLUDE[vstecmsbuild](../../extensibility/internals/includes/vstecmsbuild_md.md)] projeto pode usar [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] o mecanismo de compilação para permitir que os usuários construam a partir e na linha de comando.

## <a name="related-sections"></a>Seções relacionadas
- [Suporte a ferramentas de navegação por símbolos](../../extensibility/internals/supporting-symbol-browsing-tools.md)

 Explica a arquitetura de ferramentas de visualização de código, como o **Navegador de Objeto** e a janela **Exibição de classe.** Descreve as interfaces e métodos usados para implementar a navegação de objetos em um VSPackage.

- [Adicionar modelos de itens de projeto e projeto](../../extensibility/internals/adding-project-and-project-item-templates.md)

 Discute a importância que os projetos desempenham na determinação de qual editor é usado quando um item do projeto é aberto e como os recursos do projeto podem ser manipulados.

- [Instale vspackages com o instalador do Windows](../../extensibility/internals/installing-vspackages-with-windows-installer.md)

 Mostra como dar ao seu VSPackage sua própria identidade única e como envolver seus DLLs vspackage e outras informações em um pacote do Windows Installer (*. Arquivo MSI)* para implantação em seus clientes.

- [Hierarquias no Visual Studio](../../extensibility/internals/hierarchies-in-visual-studio.md)

 Descreve como [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] visualizae e aborda hierarquias.

- [VSPackages](../../extensibility/internals/vspackages.md)

 Fornece uma visão geral de um VSPackage, um [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] objeto COM instalado que amplia o ambiente e discute como implementar seu próprio VSPackage.

- [Tipos de projetos](../../extensibility/internals/project-types.md)

 Discute como usar projetos para modificar código, compilar e construir código, executar e depurar código, e fornece links para tópicos detalhados sobre como criar tipos de projetos.
