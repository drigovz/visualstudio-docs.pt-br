---
title: Estado de VSPackage | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: devlang-csharp
ms.topic: conceptual
helpviewer_keywords:
- state, VSPackages
- VSPackages, managing application state
- state persistence
ms.assetid: 6056a9ea-e7a8-481c-9fc8-340229fa12d9
caps.latest.revision: 25
manager: jillfra
ms.openlocfilehash: f3140b527673f87b1d7c552e99584232494aed7f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "62979989"
---
# <a name="vspackage-state"></a>Estado de VSPackage
Muitos fatores determinam o conjunto de valores persistentes ou estado de um [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] aplicativo.  
  
- Projetos têm propriedades de projeto e configuração.  
  
- As soluções têm propriedades.  
  
- As configurações de usuário determinam o tamanho e a posição das janelas de documentos, janelas de ferramentas, estado de encaixe e atalhos de teclado.  
  
- Os aplicativos podem ter opções que um usuário define.  
  
- Os objetos que um aplicativo cria podem ter propriedades próprias.  
  
  Aqui estão algumas maneiras pelas quais um [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] estado de aplicativo pode ser gerenciado:  
  
- Por meio das páginas de propriedades do projeto e da solução.  
  
- Por meio do **Assistente de importação e exportação de configurações**, que permite que um usuário mova as configurações de um computador para outro.  
  
- Por meio da caixa de diálogo **Opções** , que inclui opções relacionadas aos aplicativos.  
  
- Por meio da janela **Propriedades** , que expõe as propriedades de objetos.  
  
- Por meio da automação. Um aplicativo pode acessar VSPackage e propriedades de objeto que foram expostas para automação.  
  
  Subjacente o estado do aplicativo são vários mecanismos de persistência que permitem que o estado do aplicativo seja salvo e restaurado.  
  
## <a name="in-this-section"></a>Nesta seção  
 [Suporte para persistência de estado](../misc/support-for-state-persistence.md)  
 Lista estratégias comuns para salvar, restaurar e redefinir o estado de um VSPackage.  
  
 [Opções e páginas de opções](../extensibility/internals/options-and-options-pages.md)  
 Apresenta as páginas de opções geral e personalizadas e explica como implementá-las.  
  
 [Criar uma página de opções](../extensibility/creating-an-options-page.md)  
 Explica como criar duas páginas de opções, uma página simples e uma página personalizada.  
  
 [Suporte para categorias de configurações](../misc/support-for-settings-categories.md)  
 Discute as configurações do usuário e como elas são criadas e persistidas.  
  
 [Criar uma categoria de configurações](../extensibility/creating-a-settings-category.md)  
 Explica como criar uma [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] categoria de configurações e usá-la para salvar valores e restaurar valores de um arquivo de configurações.  
  
 [Estender propriedades e a janela de propriedades](../extensibility/extending-properties-and-the-property-window.md)  
 Explica como exibir e alterar o valor de um objeto na janela **Propriedades** .  
  
 [Expor propriedades à janela de propriedades](../extensibility/exposing-properties-to-the-properties-window.md)  
 Explica como expor as propriedades públicas de um objeto para a janela **Propriedades** .  
  
 [Suporte para propriedades do projeto e de configuração](../extensibility/internals/support-for-project-and-configuration-properties.md)  
 Explica como exibir e alterar o projeto e as propriedades de configuração.  
  
 [Obter propriedades do projeto](../extensibility/getting-project-properties.md)  
 Orienta você pelas etapas de criação de um VSPackage gerenciado que exibe as propriedades do projeto em uma janela de ferramentas.  
  
 [Usar o armazenamento de configurações](../extensibility/using-the-settings-store.md)  
 Explica o mecanismo de persistência do armazenamento de configurações e como usá-lo.  
  
## <a name="related-sections"></a>Seções relacionadas  
 [VSPackages](../extensibility/internals/vspackages.md)  
 Fornece uma orientação geral para tópicos que explicam como criar e usar o VSPackages.