---
title: Extensões de carregado automaticamente de forma síncrona
ms.date: 02/16/2019
ms.topic: conceptual
ms.assetid: 822e3cf8-f723-4ff1-8467-e0fb42358a1f
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 960fd54564bc25a8338461c30cd8a893e277b5a5
ms.sourcegitcommit: 23feea519c47e77b5685fec86c4bbd00d22054e3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/26/2019
ms.locfileid: "56844576"
---
# <a name="synchronously-autoloaded-extensions"></a>Extensões de carregado automaticamente de forma síncrona

Forma síncrona carregado automaticamente extensões têm um impacto negativo no desempenho do Visual Studio e devem ser convertidas para usar o autoload assíncrono em vez disso. A partir do Visual Studio 2019 Preview 2, as usuários serão notificados quando uma extensão está sendo sincronicamente carregados automaticamente. A extensão carregará e funcionar normalmente.

![Aviso de compatibilidade de extensão](media/extension-compatibility-warning.png)

1. Os usuários podem clicar em **Saiba mais** para acessar essa página de informações.

3. Os usuários podem clicar em **gerenciar o desempenho** para abrir o [caixa de diálogo Gerenciador de desempenho](#performance-manager-dialog) que mostra os problemas de desempenho com extensões e janelas de ferramentas.

3. Os usuários podem clicar em **não mostrar esta mensagem novamente** para ignorar a notificação. Escolher essa opção também impedirá que todas as notificações futuras de forma síncrona carregado automaticamente extensões. Os usuários continuarão a receber notificações sobre outros recursos do Visual Studio.

### <a name="performance-manager-dialog"></a>Caixa de diálogo Gerenciador de desempenho

  ![caixa de diálogo de Gerenciador de desempenho](media/performance-manager.png)

Todas as extensões de forma síncrona carregados todos os pacotes em todas as sessões de usuário serão exibidos na **APIs preteridas** guia.

* Os usuários podem clicar na **para obter mais informações sobre esse problema** para obter mais informações sobre as APIs obsoletas.
* Os usuários podem contate seus fornecedores de extensão para o andamento da migração.

Os autores de extensão podem encontrar instruções sobre como migrar pacotes para autoload assíncrono no [migrar para o AsyncPackage](https://github.com/Microsoft/VSSDK-Extensibility-Samples/tree/master/AsyncPackageMigration).
