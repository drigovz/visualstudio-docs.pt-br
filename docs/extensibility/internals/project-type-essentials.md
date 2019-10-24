---
title: Tipo de projeto Essentials | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- project types [Visual Studio SDK]
ms.assetid: 09991589-2300-430e-b6a4-7f2b95fe676f
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 435d3ca0e35911754cac1e37abb276939109a0b3
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72725405"
---
# <a name="project-type-essentials"></a>Conceitos básicos do tipo de projeto
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] inclui vários tipos de projeto para linguagens como [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] ou [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)]. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] também permite que você crie seus próprios tipos de projeto.

 Se você quiser apenas adicionar comandos personalizados, editores ou janelas de ferramentas a [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], poderá fazer isso sem criar um novo tipo de projeto. Para mais informações, consulte os seguintes tópicos:

- [Comandos, menus e barras de ferramentas](../../extensibility/internals/commands-menus-and-toolbars.md)

- [Editor e extensões do serviço de linguagem](../../extensibility/editor-and-language-service-extensions.md)

- [Ampliar e personalizar janelas de ferramentas](../../extensibility/extending-and-customizing-tool-windows.md)

  Da mesma forma, se você quiser personalizar o comportamento dos tipos de projeto [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] e [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] fornecidos, poderá fazer isso usando subtipos de projeto. Para obter mais informações, consulte [subtipos de projeto](../../extensibility/internals/project-subtypes.md).

  Você deve criar um novo tipo de projeto para projetos baseados em um idioma diferente de [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] e [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] se desejar oferecer suporte a um ou mais dos seguintes itens:

- Build

- Implantação

- Várias configurações

- Controle do código-fonte

- Depuração

- Itens de projeto no Gerenciador de Soluções

- As caixas de diálogo **Abrir projeto** ou **novo projeto**

- Aninhamento de projetos

- Para obter mais informações sobre os recursos de tipos de projeto, consulte o seguinte:

- Os tipos de projeto são objetos em um VSPackage que implementam o conjunto de interfaces [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] espera. Se você estiver usando C# o para desenvolver um tipo de projeto, as classes de projeto de estrutura de pacote gerenciado implementarão as interfaces necessárias para você e permitirá que você herde essa implementação. Para obter mais informações, consulte [usando a estrutura de pacote gerenciado para implementar um tipoC#de projeto ()](../../extensibility/internals/using-the-managed-package-framework-to-implement-a-project-type-csharp.md).

- Para C++ os desenvolvedores, as classes na biblioteca HierUtil funcionam de maneira semelhante. Para obter mais informações, consulte [não está na compilação: usando classes de projeto HierUtil7 para implementar umC++tipo de projeto ()](https://msdn.microsoft.com/library/a5c16a09-94a2-46ef-87b5-35b815e2f346).

- Os tipos de projeto podem dar suporte a dados diferentes de arquivos de código-fonte típicos que se baseiam em um assembly. exe ou. dll. Por exemplo, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] projetos de banco de dados contêm referências a arquivos de script e de consulta armazenados em disco e adicionar comandos a **Gerenciador de soluções** para executar os scripts e consultas em um banco de dados, mas os projetos não dão suporte ao comportamento de compilação. Para obter mais informações, consulte [abrindo e salvando itens de projeto](../../extensibility/internals/opening-and-saving-project-items.md).

- Um tipo de projeto não precisa usar arquivos. Por exemplo, um tipo de projeto pode armazenar todos os seus dados em um banco de dado. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] fornece aos tipos de projeto controle total sobre como eles mantêm dados para projetos e itens de projeto. Para obter mais informações, consulte [Project Type design decisions](../../extensibility/internals/project-type-design-decisions.md).

- Os tipos de projeto devem fornecer uma *fábrica de projetos*, que é um objeto que cria uma instância do tipo de projeto sempre que [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] é instruído a abrir ou criar um projeto baseado nesse tipo de projeto. Para obter mais informações, consulte [criando instâncias de projeto usando fábricas de projeto](../../extensibility/internals/creating-project-instances-by-using-project-factories.md).

- Os tipos de projeto devem fornecer modelos para projetos e itens de projeto. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] usa os modelos quando os usuários criam novos projetos e adicionam novos itens a projetos existentes. Para obter mais informações, consulte [adicionando projeto e modelos de item de projeto](../../extensibility/internals/adding-project-and-project-item-templates.md).

- Os tipos de projeto podem dar suporte a várias configurações, como Debug e Release. Os usuários podem alterar as diferentes configurações de um projeto usando as páginas de propriedades fornecidas por você. Para obter mais informações, consulte [Gerenciando opções de configuração](../../extensibility/internals/managing-configuration-options.md).

## <a name="see-also"></a>Consulte também
- [Implantar tipos de projeto](../../extensibility/internals/deploying-project-types.md)