---
title: Estendendo propriedades | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Properties window, providing support
ms.assetid: 68e2cbd4-861c-453f-8c9f-4ab6afc80e67
caps.latest.revision: 19
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: b5d2e7d15f7b479941c3186d8cd694c92f762bbf
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65690989"
---
# <a name="extending-properties"></a>Estendendo propriedades
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

A [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] janela **Propriedades** é um navegador de propriedades universal para componentes com e com+ e dá suporte a todos os [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] produtos. A janela **Propriedades** funciona com `ITypeInfo` informações de tipo e metadados com+ para listar as propriedades de tempo de design para o objeto atualmente selecionado em qualquer outra janela no IDE (ambiente de desenvolvimento integrado).  
  
 A janela **Propriedades** , que pode ser aberta pressionando-se F4 no teclado, ou selecionando **janela Propriedades** no menu **Exibir** , é usada para exibir e editar propriedades de tempo de design, independentes de configuração e eventos de objetos selecionados. Propriedades dependentes de configuração, associadas a soluções e projetos, são exibidas em [páginas de propriedades](../../extensibility/internals/property-pages.md). Para obter mais informações, consulte [NIB: Project Properties](https://msdn.microsoft.com/fb126574-24ad-4c96-9b2b-6e1f3879ba50), [Gerenciando opções de configuração](../../extensibility/internals/managing-configuration-options.md)e [NIB: item Management in Projects](https://msdn.microsoft.com/762e606b-7f44-4b66-97a1-e30a703654a0).  
  
 ![Visão geral da janela Propriedades](../../extensibility/internals/media/vspropertieswindow.png "vsPropertiesWindow")  
Janela de Propriedades  
  
 Esta seção fornece informações detalhadas relacionadas às áreas individuais da janela **Propriedades** e às interfaces que você deve implementar e chamar para popular a janela.  
  
## <a name="in-this-section"></a>Nesta seção  
 [Visão geral da janela Propriedades](../../extensibility/internals/properties-window-overview.md)  
 Explica a finalidade da janela **Propriedades** em relação à janela de ferramentas e à janela do documento.  
  
 [Política de modelo e a janela Propriedades](../../extensibility/internals/template-policy-and-the-properties-window.md)  
 Discute como um projeto está contido em um projeto de modelo empresarial e como esse projeto de modelo corporativo pode impor a política.  
  
 [Interfaces e campos da janela Propriedades](../../extensibility/internals/properties-window-fields-and-interfaces.md)  
 Explica a base para a seleção que determina quais informações são exibidas na janela **Propriedades** .  
  
 [Lista de objetos de janela Propriedades](../../extensibility/internals/properties-window-object-list.md)  
 Descreve a finalidade da lista de objetos da janela **Propriedades** , descrevendo como, quando um objeto diferente dessa lista disparar uma chamada, o ambiente é informado de que um novo objeto foi selecionado.  
  
 [Botões da janela Propriedades](../../extensibility/internals/properties-window-buttons.md)  
 Explica a finalidade dos quatro botões padrão exibidos na barra de ferramentas da janela **Propriedades** .  
  
 [Grade de exibição de propriedades](../../extensibility/internals/properties-display-grid.md)  
 Explica onde os campos nomes de propriedade e valores de propriedade são encontrados na grade.  
  
 [Anunciando o acompanhamento da seleção da janela Propriedades](../../misc/announcing-property-window-selection-tracking.md)  
 Descreve o controle de seleção para a janela **Propriedades** .  
  
 [Ocultar propriedades que têm propriedades filho](../../misc/hiding-properties-that-have-child-properties.md)  
 Explica como ocultar propriedades que têm propriedades filho implementando a <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing> interface.  
  
 [Fornecendo uma janela Propriedades personalizada](../../misc/providing-a-custom-properties-window.md)  
 Detalha as etapas para fornecer seu próprio navegador de propriedades.  
  
 [Obtendo descrições dos campos na janela Propriedades](../../misc/getting-field-descriptions-from-the-properties-window.md)  
 Explica onde encontrar a área de descrição que exibe informações relacionadas ao campo de propriedade selecionado.  
  
 [Atualizando valores de propriedade na janela Propriedades](../../misc/updating-property-values-in-the-properties-window.md)  
 Oferece instruções passo a passo que mostram as duas maneiras de manter a janela de **Propriedades** sincronizada com as alterações de valor de propriedade.  
  
## <a name="related-sections"></a>Seções relacionadas  
 [Tipos de Projeto](../../extensibility/internals/project-types.md)  
 Discute projetos como os blocos de construção do [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] IDE.  
  
 [Compilando e criando](../../ide/compiling-and-building-in-visual-studio.md)  
 Descreve como você pode usar a [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] plataforma para testar continuamente e depurar aplicativos à medida que os cria.  
  
 [Propriedades de documento HTML, a janela de propriedades](https://msdn.microsoft.com/library/46e3d164-a1a7-42f9-87b0-344e10a37b62)  
 Fornece instruções para editar um documento HTML diretamente do janela Propriedades e fornece uma tabela detalhando os campos em um documento HTML na janela Propriedades.  
  
 [IDispatch](https://msdn.microsoft.com/ebbff4bc-36b2-4861-9efa-ffa45e013eb5)  
 Descreve a `IDispatch` interface, que foi projetada primeiro para oferecer suporte à automação, fornecendo um mecanismo de ligação tardia para acessar e recuperar informações sobre os métodos e as propriedades de um objeto.  
  
 [NIB: introdução às propriedades dinâmicas (Visual Studio)](https://msdn.microsoft.com/f5102027-1431-4195-ae40-9b991de46d3a)  
 Fornece uma visão geral das propriedades dinâmicas que permitem configurar seu aplicativo para que os valores de propriedade sejam armazenados em um arquivo de configuração externo em vez do código compilado do aplicativo.  
  
 [NIB: projetos como contêineres](https://msdn.microsoft.com/87d40f63-f487-4767-8963-64beec27ba1b)  
 Descreve a função do projeto como um contêiner em uma solução para gerenciar, compilar e depurar logicamente os itens que compõem seu aplicativo.  
  
 [NIB: propriedades do projeto](https://msdn.microsoft.com/fb126574-24ad-4c96-9b2b-6e1f3879ba50)  
 Descreve como o projeto gerencia as configurações que permitem controlar as propriedades que se aplicam ao projeto inteiro e também propriedades que são limitadas a determinadas configurações de compilação do projeto.  
  
 [Soluções e projetos](../../ide/solutions-and-projects-in-visual-studio.md)  
 Explica como [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] o gerencia com eficiência os itens como referências, conexões de dados, pastas e arquivos que são necessários para seu esforço de desenvolvimento por meio de soluções e projetos.  
  
 [Estender outras partes do Visual Studio](../../extensibility/extending-other-parts-of-visual-studio.md)  
 Explica como usar [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] os serviços do para criar elementos de interface do usuário que correspondam ao restante do [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] .
