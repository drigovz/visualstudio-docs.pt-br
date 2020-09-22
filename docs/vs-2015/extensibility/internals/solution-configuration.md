---
title: Configuração da solução | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- solution configurations
ms.assetid: f22cfc75-3e31-4e0d-88a9-3ca99539203b
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: bbd47969a7a48be817e8e2f5359705e03b5d0dc2
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "90838543"
---
# <a name="solution-configuration"></a>Configuração da solução
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

As configurações da solução armazenam propriedades no nível da solução. Eles direcionam o comportamento da chave **Start** (F5) e os comandos de **Build** . Por padrão, esses comandos criam e iniciam a configuração de depuração. Ambos os comandos são executados no contexto de uma configuração de solução. Isso significa que o usuário pode esperar F5 para iniciar e compilar qualquer que seja a solução ativa configurada por meio das configurações. O ambiente foi projetado para otimizar soluções em vez de projetos quando se trata de criar e executar.  
  
 A barra de ferramentas padrão do Visual Studio contém um botão Iniciar e uma lista suspensa configuração de solução à direita do botão Iniciar. Essa lista permite que os usuários escolham a configuração a ser iniciada quando F5 é pressionado, cria suas próprias configurações de solução ou edita uma configuração existente.  
  
> [!NOTE]
> Não há nenhuma interface de extensibilidade para criar ou editar as configurações da solução. É necessário usar `DTE.SolutionBuilder`. No entanto, há APIs de extensibilidade para gerenciar a compilação da solução. Para obter mais informações, consulte <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionBuildManager2>.  
  
 Veja como você pode implementar as configurações de solução com suporte pelo seu tipo de projeto:  
  
- Project  
  
   Exibe os nomes dos projetos encontrados na solução atual.  
  
- Configuração  
  
   Para fornecer a lista de configurações com suporte pelo tipo de projeto e exibidas nas páginas de propriedades, implemente <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2> .  
  
   A coluna configuração exibe o nome da configuração do projeto a ser criada nesta configuração de solução e lista todas as configurações do projeto quando você clica no botão de seta. O ambiente chama o <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2.GetCfgNames%2A> método para preencher essa lista. Se o <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2.GetCfgProviderProperty%2A> método indicar que o projeto dá suporte à edição de configuração, as seleções de novo ou editar também serão exibidas no título configuração. Cada uma dessas seleções inicia caixas de diálogo que chamam métodos da `IVsCfgProvider2` interface para editar as configurações do projeto.  
  
   Se um projeto não oferecer suporte a configurações, a coluna configuração exibirá nenhuma e será desabilitada.  
  
- Plataforma  
  
   Exibe a plataforma à qual a configuração de projeto selecionada é compilada e lista todas as plataformas disponíveis para o projeto quando você clica no botão de seta. O ambiente chama o <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2.GetPlatformNames%2A> método para preencher essa lista. Se o <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2.GetCfgProviderProperty%2A> método indicar que o projeto dá suporte à edição de plataforma, as seleções de novo ou editar também serão exibidas sob o título plataforma. Cada uma dessas seleções inicia caixas de diálogo que chamam `IVsCfgProvider2` métodos para editar as plataformas disponíveis do projeto.  
  
   Se um projeto não oferecer suporte a plataformas, a coluna plataforma para esse projeto exibirá nenhum e será desabilitada.  
  
- Build  
  
   Especifica se o projeto é ou não compilado pela configuração da solução atual. Projetos não selecionados não são criados quando os comandos de compilação no nível da solução são invocados, apesar de quaisquer dependências de projeto que eles contêm. Os projetos não selecionados para serem criados ainda estão incluídos na depuração, execução, empacotamento e implantação da solução.  
  
- Implantar  
  
   Especifica se o projeto será ou não implantado quando os comandos iniciar ou implantar forem usados com a configuração de compilação da solução selecionada. A caixa de seleção desse campo estará disponível se o projeto der suporte à implantação implementando a <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg> interface em seu <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg2> objeto.  
  
  Depois que uma nova configuração de solução for adicionada, o usuário poderá selecioná-la na caixa de listagem suspensa configuração de solução na barra de ferramentas padrão para criar e/ou iniciar essa configuração.  
  
## <a name="see-also"></a>Consulte Também  
 [Gerenciando opções de configuração](../../extensibility/internals/managing-configuration-options.md)   
 [Configuração do projeto para compilação](../../extensibility/internals/project-configuration-for-building.md)   
 [Objeto de configuração de projeto](../../extensibility/internals/project-configuration-object.md)
