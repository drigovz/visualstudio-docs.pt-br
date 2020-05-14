---
title: Ampliação de Propriedades | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Properties window, providing support
ms.assetid: 68e2cbd4-861c-453f-8c9f-4ab6afc80e67
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7064128c54434b0a7bb8799e62b751e765511c48
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80708428"
---
# <a name="extend-properties"></a>Estender propriedades
A [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] janela **Propriedades** é um navegador de propriedade universal para [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] componentes COM e COM+ e suporta todos os produtos. A **Properties** janela Propriedades `ITypeInfo` funciona com informações de tipo e metadados COM+ para listar as propriedades de tempo de projeto para o objeto selecionado atualmente em qualquer outra janela no ambiente de desenvolvimento integrado (IDE).

 A janela **Propriedades,** que pode ser aberta pressionando **F4** no teclado ou selecionando **Janelas de Propriedades** no menu **Exibir,** é usada para visualizar e editar propriedades e eventos independentes de configuração, tempo de design e eventos de objetos selecionados. Propriedades dependentes da configuração, associadas a soluções e projetos, são exibidas em [páginas de propriedade](../../extensibility/internals/property-pages.md). Para obter mais informações, [gerencie opções de configuração](../../extensibility/internals/managing-configuration-options.md).

 ![Visão geral da janela de propriedades](../../extensibility/internals/media/vspropertieswindow.png "vsPropertiesWindow") Janela de propriedades

 Esta seção fornece informações detalhadas relacionadas às áreas individuais da janela **Propriedades** e às interfaces que você deve implementar e chamar para preencher a janela.

## <a name="in-this-section"></a>Nesta seção
- [Visão geral da janela de propriedades](../../extensibility/internals/properties-window-overview.md)

 Explica o propósito da janela **Propriedades** em relação à janela da ferramenta e à janela do documento.

- [Política de modelo e a janela Propriedades](../../extensibility/internals/template-policy-and-the-properties-window.md)

 Discute como um projeto está contido em um projeto de modelo corporativo e como esse projeto de modelo corporativo pode impor a política.

- [Propriedades campos de janelas e interfaces](../../extensibility/internals/properties-window-fields-and-interfaces.md)

 Explica a base de seleção que determina quais informações são exibidas na janela **Propriedades.**

- [Lista de objetos da janela propriedades](../../extensibility/internals/properties-window-object-list.md)

 Descreve o propósito da lista de objetos da janela **Propriedades,** descrevendo como, quando um objeto diferente desta lista aciona uma chamada, o ambiente é informado de que um novo objeto foi selecionado.

- [Botões de janela de propriedades](../../extensibility/internals/properties-window-buttons.md)

 Explica o propósito dos quatro botões padrão exibidos na barra de ferramentas da janela **Propriedades.**

- [Grade de exibição de propriedades](../../extensibility/internals/properties-display-grid.md)

 Explica onde os nomes da propriedade e os valores da propriedade são encontrados na grade.

## <a name="related-sections"></a>Seções relacionadas
- [Tipos de projetos](../../extensibility/internals/project-types.md)

 Discute projetos como os blocos de construção do [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE.

- [Compilação e construção](../../ide/compiling-and-building-in-visual-studio.md)

 Descreve como você pode [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] usar a plataforma para testar e depurar continuamente aplicativos à medida que você os constrói.

- [IDispatch](/previous-versions/windows/desktop/api/oaidl/nn-oaidl-idispatch)

 Descreve a `IDispatch` interface, que foi projetada inicialmente para suportar a automação, fornecendo um mecanismo vinculado tardio para acessar e recuperar informações sobre os métodos e propriedades de um objeto.

- [Gerenciar configurações de aplicativo (.NET)](../../ide/managing-application-settings-dotnet.md)

 Fornece uma visão geral das configurações do aplicativo que permitem configurar seu aplicativo para que os valores de propriedade sejam armazenados em um arquivo de configuração externa em vez do código compilado do aplicativo.

- [Soluções e projetos](../../ide/solutions-and-projects-in-visual-studio.md)

 Explica [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] como gerencia eficientemente os itens, como referências, conexões de dados, pastas e arquivos que são exigidos pelo seu esforço de desenvolvimento através de soluções e projetos.

- [Estender outras partes do Visual Studio](../../extensibility/extending-other-parts-of-visual-studio.md)

 Explica como [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] usar serviços para criar elementos [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]de IU que correspondem ao resto do .
