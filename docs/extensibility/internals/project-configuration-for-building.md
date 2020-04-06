---
title: Configuração do projeto para construção | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], configuration for building
- project configurations, building
ms.assetid: 2c83615d-fa4d-4b9f-b315-7a69b3000da0
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: bdd084053e06206a99298b234b4d51c8504119a2
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80706729"
---
# <a name="project-configuration-for-building"></a>Configuração de projeto para compilar
A lista de configurações de solução para uma determinada solução é gerenciada pela caixa de diálogo Configurações de solução.

 Um usuário pode criar configurações adicionais de solução, cada uma com seu próprio nome único. Quando o usuário cria uma nova configuração de solução, o IDE é padrão para o nome de configuração correspondente nos projetos ou Depurar se não houver nome correspondente. O usuário pode alterar a seleção para atender a requisitos específicos, se necessário. A única exceção a esse comportamento é quando o projeto suporta uma configuração que corresponda ao nome da nova configuração da solução. Por exemplo, suponha que uma solução contenha Project1 e Project2. O Project1 tem configurações de projeto Debug, Retail e MyConfig1. O Project2 tem configurações de projeto Debug, Retail e MyConfig2.

 Se o usuário criar uma nova configuração de solução chamada MyConfig2, o Project1 vinculará sua configuração de Depuração à configuração da solução por padrão. O Project2 também vincula sua configuração MyConfig2 à configuração da solução por padrão.

> [!NOTE]
> A ligação é insensível ao caso.

 Quando o usuário seleciona o item **Seleção múltipla** na lista de itens de desuso de configuração, o ambiente exibe uma caixa de diálogo que fornece a lista de configurações disponíveis.

 ![Múltiplas configurações](../../extensibility/internals/media/vsmultiplecfgs.gif "vsMultipleCfgs") Múltiplas configurações

 Nesta caixa de diálogo, o usuário pode selecionar uma ou várias configurações. Uma vez selecionados, os valores de propriedade exibidos na caixa de diálogo páginas de propriedade refletem a interseção de valores para as configurações selecionadas.

 Consulte [configuração de solução](../../extensibility/internals/solution-configuration.md) para obter informações relacionadas à adição e renomeação de configurações para soluções e projetos.

 Dependências de projetos e ordem de construção são independentes de configuração de solução: ou seja, você só pode configurar uma árvore de dependência para todos os projetos na solução. Clicar com o botão direito do mouse na solução ou no projeto e selecionar a opção **Dependências de Projeto** ou **Ordem de Construção de Projeto** abre a caixa de diálogo Dependências do **projeto.** Também pode ser aberto a partir do menu **do Projeto.**

 ![Dependências do Projeto](../../extensibility/internals/media/vsprojdependencies.gif "vsProjDependencies") Dependências do projeto

 As dependências do projeto determinam a ordem em que os projetos são construídos. Use a guia 'Criar ordem na caixa de diálogo' para visualizar a ordem exata na qual os projetos dentro de uma solução serão construídos e use a guia Dependências para modificar a ordem de compilação.

> [!NOTE]
> Projetos na lista que têm suas caixas de seleção selecionadas, mas aparecem escurecidos, foram adicionados pelo ambiente devido a dependências explícitas especificadas pelas interfaces <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildDependency> ou não <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployDependency> podem ser alterados. Por exemplo, adicionar uma [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] referência de projeto a outro projeto adiciona automaticamente uma dependência de compilação que só pode ser removida excluindo a referência. Projetos cujas caixas de seleção são claras e parecem escurecidas não podem ser selecionados porque isso criaria um loop de dependência (por exemplo, o Project1 dependeria do Project2, e o Project2 dependeria do Project1), o que atrasaria a construção.

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]os processos de compilação e link típicos que são invocados com um único comando Build. Dois outros processos de compilação também podem ser suportados: uma operação limpa para excluir todos os itens de saída de uma compilação anterior e uma verificação atualizada para determinar se um item de saída em uma configuração foi alterado.

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg2>objetos retornam <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildableProjectCfg> um correspondente <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg2.get_CfgType%2A>(retornado) para gerenciar seus processos de compilação. Para relatar o status de uma operação de compilação <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildStatusCallback>enquanto ela está ocorrendo, as configurações fazem chamadas para, uma interface implementada pelo ambiente e qualquer outro objeto interessado em criar eventos de status.

 Uma vez construídas, as configurações podem ser usadas para determinar se podem ou não ser executadas sob o controle do depurador. Configurações <xref:Microsoft.VisualStudio.Shell.Interop.IVsDebuggableProjectCfg> implementadas para suportar a depuração.

 Depois de implementar as dependências do projeto, você pode manipular programáticamente as dependências através do modelo de automação. Você <xref:EnvDTE.SolutionBuild.BuildDependencies%2A> chama o modelo de automação. Não há interfaces de nível de API VSIP disponíveis que permitam a manipulação direta das configurações do gerenciador de compilação de soluções e suas propriedades.

 Além disso, você pode fornecer uma grade na janela de dependências do projeto. Para obter mais informações, consulte [Properties Display Grid](../../extensibility/internals/properties-display-grid.md).

## <a name="see-also"></a>Confira também
- [Gerenciando opções de configuração](../../extensibility/internals/managing-configuration-options.md)
- [Configuração de projeto para gerenciar a implantação](../../extensibility/internals/project-configuration-for-managing-deployment.md)
- [Configuração de projeto para saída](../../extensibility/internals/project-configuration-for-output.md)
