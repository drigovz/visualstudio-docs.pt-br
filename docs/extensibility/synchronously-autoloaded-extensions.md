---
title: Extensões carregadas automaticamente de modo sincrônico
ms.date: 12/11/2019
ms.topic: conceptual
ms.assetid: 822e3cf8-f723-4ff1-8467-e0fb42358a1f
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 71ba7e8ee1b847137386c7714745f6668be4cabc
ms.sourcegitcommit: c150d0be93b6f7ccbe9625b41a437541502560f5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/10/2020
ms.locfileid: "75848730"
---
# <a name="synchronously-autoloaded-extensions"></a>Extensões carregadas automaticamente de modo sincrônico

As extensões autocarregadas de forma síncrona têm um impacto negativo sobre o desempenho do Visual Studio e devem ser convertidas para usar a autocarregamento assíncrona em vez disso. Por padrão, o Visual Studio 2019 bloqueia pacotes carregados de forma síncrona de qualquer extensão e notifica o usuário.

![aviso de compatibilidade de extensão](media/extension-compatibility-warning-16-1.png.png)

Você pode:

- Clique em **permitir AutoLoad síncrona** para permitir que as extensões sejam AutoLoad. Para alterar essa configuração nas opções do Visual Studio, clique em ambiente, clique em extensões e marque a caixa de seleção "permitir AutoLoad síncrona de extensões". 

- Clique em **gerenciar desempenho** para abrir a [caixa de diálogo Gerenciador de desempenho](#performance-manager-dialog) que mostra problemas de desempenho com extensões e janelas de ferramentas.

- Clique em **não mostrar esta mensagem para as extensões atuais** para ignorar a notificação e evitar notificações futuras de extensões instaladas existentes. Se você adicionar uma nova extensão que é carregada de forma síncrona, essa notificação será exibida novamente. Você continuará a receber notificações sobre outros recursos do Visual Studio.

## <a name="performance-manager-dialog"></a>Caixa de diálogo Gerenciador de desempenho

![caixa de diálogo Gerenciador de desempenho](media/performance-manager.png)

Todas as extensões que carregaram de forma síncrona todos os pacotes em todas as sessões de usuário são exibidas na guia **APIs preteridas** .

* Clique em **mais informações sobre esse problema** para coletar mais informações sobre as APIs preteridas.
* Entre em contato com seus fornecedores de extensão para o andamento da migração.

## <a name="specify-synchronous-autoload-settings-using-group-policy"></a>Especificar configurações de AutoLoad síncronas usando a política de grupo

Os administradores podem habilitar um Política de Grupo para permitir a AutoLoad síncrona. Para fazer isso, defina uma política baseada no Registro na seguinte chave:

**HKEY_LOCAL_MACHINE\SOFTWARE\Policies\Microsoft\VisualStudio\SynchronousAutoload**

Entrada = **permitido**

Valor = (DWORD)
* **0** não é permitido AutoLoad síncrono
* **1** é permitida a AutoLoad síncrona

## <a name="extension-authors"></a>Autores de extensão
Os autores de extensão podem encontrar instruções para migrar pacotes para AutoLoad assíncrona em [migrar para o AsyncPackage](https://github.com/Microsoft/VSSDK-Extensibility-Samples/tree/master/AsyncPackageMigration).

## <a name="see-also"></a>Veja também
Para obter mais informações sobre as configurações de AutoLoad síncronas no Visual Studio 2019, consulte a página [comportamento de AutoLoad síncrona](https://devblogs.microsoft.com/visualstudio/updates-to-synchronous-autoload-of-extensions-in-visual-studio-2019/) .
