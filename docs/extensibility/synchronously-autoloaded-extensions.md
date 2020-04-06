---
title: Extensões carregadas automaticamente de modo sincrônico
ms.date: 12/11/2019
ms.topic: conceptual
ms.assetid: 822e3cf8-f723-4ff1-8467-e0fb42358a1f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ab62d235fd6ed4e47e765fc23868acd5c56efcb2
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80699378"
---
# <a name="synchronously-autoloaded-extensions"></a>Extensões carregadas automaticamente de modo sincrônico

As extensões carregadas de forma sincronizada e automática têm um impacto negativo no desempenho do Visual Studio e devem ser convertidas para usar carga automática assíncrona. Por padrão, o Visual Studio 2019 bloqueia pacotes carregados sincronicamente de qualquer extensão e notifica o usuário.

![aviso de compatibilidade de extensão](media/extension-compatibility-warning-16-1.png.png)

Você pode:

- Clique em Permitir a **carga automática síncrona** para permitir que as extensões carreguem automaticamente. Para alterar essa configuração nas opções do Visual Studio, clique em Ambiente e clique em Extensões e selecione a caixa de seleção "Permitir carga automática síncrona de extensões". 

- Clique em **Gerenciar o desempenho** para abrir a caixa de diálogo [Gerenciador de desempenho](#performance-manager-dialog) que mostra problemas de desempenho com extensões e janelas de ferramentas.

- Clique em **Não mostrar esta mensagem para extensões atuais** para descartar a notificação e impedir que notificações futuras de extensões instaladas existentes. Se você adicionar uma nova extensão que seja carregada de forma sincronizada, esta notificação será exibida novamente. Você continuará recebendo notificações sobre outros recursos do Visual Studio.

## <a name="performance-manager-dialog"></a>Diálogo gerenciador de desempenho

![diálogo gerente de desempenho](media/performance-manager.png)

Todas as extensões que carregaram sincronizadamente quaisquer pacotes em qualquer sessão de usuário aparecem na guia **APIs depreciada.**

* Clique em **Mais informações sobre este problema** para coletar mais informações sobre as APIs depreciadas.
* Entre em contato com seus fornecedores de extensão para o progresso da migração.

## <a name="specify-synchronous-autoload-settings-using-group-policy"></a>Especificar configurações de carga automática síncronas usando a diretiva de grupo

Os administradores podem habilitar uma Diretiva de Grupo para permitir a carga automática síncrona. Para fazer isso, defina uma política baseada no Registro na seguinte chave:

**HKEY_LOCAL_MACHINE\SOFTWARE\Policies\Microsoft\VisualStudio\SynchronousAutoload**

Entrada = **Permitida**

Valor = (DWORD)
* **0** é autoload síncrono não permitido
* **1** é a carga automática síncrona permitida

## <a name="extension-authors"></a>Autores de extensão
Os autores de extensão podem encontrar instruções para migrar pacotes para carga automática assíncrona em [Migrar para AsyncPackage](https://github.com/Microsoft/VSSDK-Extensibility-Samples/tree/master/AsyncPackageMigration).

## <a name="see-also"></a>Confira também
Para obter mais informações sobre as configurações de carga automática síncrona no Visual Studio 2019, consulte a página [Comportamento de Carga Automática Síncrona.](https://devblogs.microsoft.com/visualstudio/updates-to-synchronous-autoload-of-extensions-in-visual-studio-2019/)
