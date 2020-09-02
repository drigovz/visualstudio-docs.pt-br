---
title: Diretrizes de manutenção para aplicativos de shell isolados | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio Shell integrated mode, serviceability
- Shell integrated mode [Visual Studio], serviceability
ms.assetid: 747d1a47-b8b3-4e8b-93c0-768724be48f2
caps.latest.revision: 16
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 093690c293ff6857eedc50d5eccc793d7d5bb114
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68159277"
---
# <a name="servicing-guidelines-for-isolated-shell-applications"></a>Diretrizes de manutenção para aplicativos de Shell isolado
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Ao distribuir um aplicativo de shell isolado do Visual Studio, você deve ser capaz de fornecer atualizações de software para seu aplicativo depois que ele é instalado. Para fazer isso, você deve instalar o aplicativo usando um arquivo do Microsoft Installer (MSI). Esse tipo de instalação permite que as atualizações de software fornecidas pela Microsoft sejam redistribuídas pelo download da Web e consumidas por seus clientes sem intervenção personalizada.  
  
## <a name="servicing-requirements"></a>Requisitos de manutenção  
 Você pode garantir que a instalação do Shell isolado possa permitir atualizações, certificando-se de que seu programa de instalação atenda aos três critérios a seguir.  
  
### <a name="redistribute-by-using-an-msi"></a>Redistribuir usando um MSI  
 Você deve usar um MSI para redistribuir seu aplicativo, pois um MSI preserva a identidade do produto e garante que o aplicativo tenha um local físico no computador cliente. Os módulos de mesclagem (arquivos. msm) não fornecem essas garantias e não devem ser usados.  
  
### <a name="accounting-for-custom-actions"></a>Contabilidade de ações personalizadas  
 As ações personalizadas são diretivas de instalação não padrão em um programa instalador. As ações personalizadas alteram parâmetros como locais de arquivos, configurações do registro, configurações do usuário ou outros itens de instalação. Ações personalizadas podem manipular dados no momento da instalação.  
  
 Ao usar ações personalizadas em um programa de instalação, você deve garantir que cada ação personalizada de tempo de instalação deve ter uma ação personalizada correspondente para desfazer a ação quando o usuário desinstala o aplicativo. Se o programa de instalação falhar ao fornecer a ação personalizada de desinstalação correspondente, a remoção do aplicativo o deixará parcialmente instalado.  
  
- Uma ação personalizada que se baseia em uma versão específica de um arquivo ou valores de hash falhará quando as atualizações de software alterarem essas versões ou valores de hash. Nesse caso, a ação personalizada deve atualizar manualmente esses valores. Um problema adicional ocorre se as versões de um arquivo ou valores de hash forem compartilhadas entre as versões do produto. Evite essa dependência sempre que possível.  
  
### <a name="accounting-for-shared-files"></a>Contabilidade de arquivos compartilhados  
 Os arquivos compartilhados têm os mesmos nomes e são instalados no mesmo local por vários produtos. Esses produtos podem diferir em versão, SKU (unidade de manutenção de estoque) ou ambos, e os produtos podem coexistir em um determinado computador. No entanto, os arquivos compartilhados criam problemas de manutenção por vários motivos:  
  
- A atualização de arquivos compartilhados pode causar problemas de compatibilidade de aplicativos porque uma atualização para um aplicativo pode alterar a versão de um arquivo usado por um segundo aplicativo que não foi atualizado. Instaladores de produtos que compartilham referências de contagem de arquivos para os arquivos compartilhados. Portanto, a desinstalação de um produto não afeta arquivos compartilhados além de decrementar a contagem de instâncias instaladas.  
  
- O instalador da QFE (Quick Fix Engineering) reverte versões de arquivos para as versões dos produtos atendidos pelo instalador QFE. Esse processo, potencialmente, interrompe um aplicativo que fornecia um arquivo compartilhado atualizado.
