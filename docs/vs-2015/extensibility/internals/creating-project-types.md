---
title: Criando tipos de projeto | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- project types, new
- projects [Visual Studio SDK], new project types
ms.assetid: bdb2d22e-d622-450c-bb2d-98152a745fcf
caps.latest.revision: 26
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: bbe65d1615603e4dc7546dbfe3530093c62528e5
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68155035"
---
# <a name="creating-project-types"></a>Criando tipos de projeto
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Você pode estender [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] criando um novo tipo de projeto. Para criar um novo tipo de projeto, você deve compreender vários conceitos e concluir várias etapas. Os tópicos a seguir fornecem uma visão geral de como criar tipos de projeto.  
  
## <a name="in-this-section"></a>Nesta seção  
 [Decisões de design do tipo de projeto](../../extensibility/internals/project-type-design-decisions.md)  
 Discute o item, a persistência de arquivo do projeto e as decisões de design mecânico de compromisso que você precisa fazer antes de criar um novo tipo de projeto.  
  
 [Lista de verificação: Criando tipos de projeto](../../extensibility/internals/checklist-creating-new-project-types.md)  
 Fornece uma visão geral das etapas que você deve seguir para criar um novo tipo de projeto que dá suporte a tarefas de programação como edição de código e compilação, criação, depuração e implantação de aplicativos em seu projeto.  
  
 [Criando instâncias de projeto por meio de fábricas de projeto](../../extensibility/internals/creating-project-instances-by-using-project-factories.md)  
 Fornece informações sobre como fornecer e usar uma fábrica de projetos para criar instâncias de um novo projeto.  
  
 [Registrando um tipo de projeto](../../extensibility/internals/registering-a-project-type.md)  
 Fornece exemplos de código de instruções do registro que fornecem caminhos e dados padrão e uma tabela que contém entradas do script de registro para cada instrução.  
  
 [Persistência de projeto](../../extensibility/internals/project-persistence.md)  
 Discute o uso de `IPersistFileFormat` para manter objetos de projeto de arquivo e não baseados em arquivo.  
  
 [Usando o MSBuild](../../extensibility/internals/using-msbuild.md)  
 Descreve como o tipo de projeto pode usar o [!INCLUDE[vstecmsbuild](../../includes/vstecmsbuild-md.md)] mecanismo de compilação para permitir que os usuários criem de [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] e na linha de comando.  
  
## <a name="related-sections"></a>Seções relacionadas  
 [Suporte a ferramentas de navegação de símbolo](../../extensibility/internals/supporting-symbol-browsing-tools.md)  
 Explica a arquitetura das ferramentas de exibição de código, como o **pesquisador de objetos** e a janela **modo de exibição de classe** . Descreve as interfaces e os métodos que são usados para implementar a navegação de objeto em um VSPackage.  
  
 [Adicionando o projeto e os modelos de item do projeto](../../extensibility/internals/adding-project-and-project-item-templates.md)  
 Discute o significado que os projetos desempenham para determinar qual editor é usado quando um item de projeto é aberto e como os recursos do projeto podem ser manipulados.  
  
 [Instalando VSPackages com o Windows Installer](../../extensibility/internals/installing-vspackages-with-windows-installer.md)  
 Mostra como dar ao seu VSPackage sua própria identidade exclusiva e como encapsular suas DLLs do VSPackage e outras informações em um pacote de Windows Installer (. Arquivo MSI) para implantação em seus clientes.  
  
 [Hierarquias no Visual Studio](../../extensibility/internals/hierarchies-in-visual-studio.md)  
 Descreve como [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Exibir e solucionar as hierarquias.  
  
 [VSPackages](../../extensibility/internals/vspackages.md)  
 Fornece uma visão geral de um VSPackage, um objeto COM instalável que estende o [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] ambiente e discute como implementar seu próprio VSPackage.  
  
 [Tipos de Projeto](../../extensibility/internals/project-types.md)  
 Discute como usar projetos para modificar código, compilar e compilar código, e executar e depurar código e fornece links para tópicos detalhados sobre como criar tipos de projeto.
