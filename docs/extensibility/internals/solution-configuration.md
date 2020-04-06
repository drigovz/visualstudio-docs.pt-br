---
title: Configuração da solução | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- solution configurations
ms.assetid: f22cfc75-3e31-4e0d-88a9-3ca99539203b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7c96b73747ef8b136a74a7256cde7fef8d1c42de
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80705386"
---
# <a name="solution-configuration"></a>Configuração da solução
Configurações de solução armazenam propriedades em nível de solução. Eles direcionam o comportamento da tecla **Start** (F5) e dos comandos **Build.** Por padrão, esses comandos constroem e iniciam a configuração de depuração. Ambos os comandos são executados no contexto de uma configuração de solução. Isso significa que o usuário pode esperar que o F5 inicie e construa qualquer que seja a solução ativa configurada através das configurações. O ambiente é projetado para otimizar soluções em vez de projetos quando se trata de construção e execução.

 A barra de ferramentas padrão do Visual Studio contém um botão Iniciar e uma configuração de solução parabaixo à direita do botão Iniciar. Esta lista permite que os usuários escolham a configuração a ser iniciada quando o F5 é pressionado, criam suas próprias configurações de solução ou editam uma configuração existente.

> [!NOTE]
> Não há interfaces de extensibilidade para criar ou editar as configurações da solução. É necessário usar `DTE.SolutionBuild`. No entanto, existem APIs de extensibilidade para gerenciar a compilação da solução. Para obter mais informações, consulte <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionBuildManager2>.

 Veja como você pode implementar as configurações de solução suportadas pelo seu tipo de projeto:

- Project

   Exibe os nomes dos projetos encontrados na solução atual.

- Configuração

   Para fornecer a lista de configurações suportadas pelo seu tipo <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2>de projeto e exibidas nas páginas de propriedade, implemente .

   A coluna Configuração exibe o nome da configuração do projeto a ser construído nesta configuração de solução e lista todas as configurações do projeto quando você clica no botão seta. O ambiente <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2.GetCfgNames%2A> chama o método para preencher esta lista. Se <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2.GetCfgProviderProperty%2A> o método indicar que o projeto suporta a edição de configuração, as seleções Nova ou Editar também serão exibidas sob o título Configuração. Cada uma dessas seleções lança caixas `IVsCfgProvider2` de diálogo que chamam métodos da interface para editar as configurações do projeto.

   Se um projeto não suportar configurações, a coluna Configuração exibe Nenhum e será desativado.

- Plataforma

   Exibe a plataforma para a configuração do projeto selecionada e lista todas as plataformas disponíveis para o projeto quando você clica no botão seta. O ambiente <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2.GetPlatformNames%2A> chama o método para preencher esta lista. Se <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2.GetCfgProviderProperty%2A> o método indicar que o projeto suporta a edição da plataforma, seleções Nova ou Editar também serão exibidas sob o título Plataforma. Cada uma dessas seleções `IVsCfgProvider2` lança caixas de diálogo que chamam métodos para editar as plataformas disponíveis do projeto.

   Se um projeto não suportar plataformas, a coluna da plataforma para esse projeto exibe Nenhum e é desativado.

- Build

   Especifica se o projeto é ou não construído pela configuração atual da solução. Os projetos não selecionados não são construídos quando os comandos de compilação em nível de solução são invocados, apesar de quaisquer dependências de projeto que contenham. Os projetos não selecionados para serem construídos ainda estão incluídos na depuração, execução, embalagem e implantação da solução.

- Implantar

   Especifica se o projeto será implantado ou não quando os comandos Iniciar ou Implantar forem usados com a configuração de compilação de solução selecionada. A caixa de seleção para este campo estará disponível <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg> se <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg2> o projeto suportar a implantação implementando a interface em seu objeto.

  Uma vez que uma nova configuração de solução é adicionada, o usuário pode selecioná-la na caixa de lista de lista de itens de isto de configuração da solução na barra de ferramentas padrão para construir e/ou iniciar essa configuração.

## <a name="see-also"></a>Confira também
- [Gerenciando opções de configuração](../../extensibility/internals/managing-configuration-options.md)
- [Configuração de projeto para compilar](../../extensibility/internals/project-configuration-for-building.md)
- [Objeto de configuração de projeto](../../extensibility/internals/project-configuration-object.md)
