---
title: Projeto Type Essentials | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- project types [Visual Studio SDK]
ms.assetid: 09991589-2300-430e-b6a4-7f2b95fe676f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b44da532207668d9526aec0ccdcab027b94184e6
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80706381"
---
# <a name="project-type-essentials"></a>Conceitos básicos do tipo de projeto
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]inclui vários tipos de projetos [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] para [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)]idiomas como ou . [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]também permite que você crie seus próprios tipos de projeto.

 Se você quiser apenas adicionar comandos personalizados, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]editores ou janelas de ferramentas para , você pode fazê-lo sem criar um novo tipo de projeto. Para obter mais informações, consulte estes tópicos:

- [Comandos, menus e barras de ferramentas](../../extensibility/internals/commands-menus-and-toolbars.md)

- [Editor e extensões do serviço de linguagem](../../extensibility/editor-and-language-service-extensions.md)

- [Ampliar e personalizar janelas de ferramentas](../../extensibility/extending-and-customizing-tool-windows.md)

  Da mesma forma, se você quiser [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] personalizar [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] o comportamento dos tipos de projeto e fornecidos, você pode fazê-lo usando subtipos de projeto. Para obter mais informações, consulte [Subtipos do Projeto](../../extensibility/internals/project-subtypes.md).

  Você deve criar um novo tipo de projeto para [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] projetos que são baseados em um idioma diferente e se você quiser apoiar um ou mais dos seguintes:

- Build

- Implantação

- Múltiplas configurações

- Controle do código-fonte

- Depuração

- Itens do projeto no Solution Explorer

- As caixas de diálogo **do Projeto Aberto** ou do Novo **Projeto**

- Aninhamento de projeto

- Para obter mais informações sobre os recursos dos tipos de projeto, consulte o seguinte:

- Os tipos de projeto são objetos em [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] um VSPackage que implementam o conjunto de interfaces que espera. Se você estiver usando C# para desenvolver um tipo de projeto, as classes de projeto Managed Package Framework implementam as interfaces necessárias para você e permitem que você herde essa implementação. Para obter mais informações, [consulte Usando o Framework de pacote gerenciado para implementar um tipo de projeto (C#)](../../extensibility/internals/using-the-managed-package-framework-to-implement-a-project-type-csharp.md).

- Para os desenvolvedores C++, as aulas na biblioteca HierUtil funcionam de maneira semelhante. Para obter mais informações, consulte [Não em Construção: Usando classes de projeto HierUtil7 para implementar um tipo de projeto (C++)](https://msdn.microsoft.com/library/a5c16a09-94a2-46ef-87b5-35b815e2f346).

- Os tipos de projeto podem suportar dados que não sejam arquivos de código-fonte típicos que se constroem em um conjunto .exe ou .dll. Por exemplo, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] os projetos de banco de dados contêm referências a arquivos de script e consulta armazenados em disco e adicionam comandos ao **Solution Explorer** para executar os scripts e consultas em um banco de dados, mas os projetos não suportam comportamento de compilação. Para obter mais informações, consulte [Itens do projeto de abertura e salvamento](../../extensibility/internals/opening-and-saving-project-items.md).

- Um tipo de projeto não precisa usar arquivos. Por exemplo, um tipo de projeto poderia armazenar todos os seus dados em um banco de dados. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]dá aos tipos de projeto controle completo sobre como eles persistem dados para projetos e itens de projeto. Para obter mais informações, consulte [Project Type Design Decisions](../../extensibility/internals/project-type-design-decisions.md).

- Os tipos de projeto devem fornecer uma *fábrica de projetos*, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] que é um objeto que cria uma instância do tipo de projeto sempre que é instruído a abrir ou criar um projeto baseado nesse tipo de projeto. Para obter mais informações, consulte [Criando instâncias de projeto usando fábricas de projetos.](../../extensibility/internals/creating-project-instances-by-using-project-factories.md)

- Os tipos de projetos devem fornecer modelos para projetos e itens do projeto. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]usa os modelos quando os usuários criam novos projetos e adicionam novos itens aos projetos existentes. Para obter mais informações, consulte [Adicionar modelos de itens de projeto e projeto](../../extensibility/internals/adding-project-and-project-item-templates.md).

- Os tipos de projeto podem suportar várias configurações, como Debug e Release. Os usuários podem alterar as diferentes configurações de um projeto usando páginas de propriedade que você fornece. Para obter mais informações, consulte [Gerenciar opções de configuração](../../extensibility/internals/managing-configuration-options.md).

## <a name="see-also"></a>Confira também
- [Tipos de projeto de implantação](../../extensibility/internals/deploying-project-types.md)
