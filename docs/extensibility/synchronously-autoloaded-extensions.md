---
title: Extensões carregadas automaticamente de modo sincrônico
ms.date: 02/16/2019
ms.topic: conceptual
ms.assetid: 822e3cf8-f723-4ff1-8467-e0fb42358a1f
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d23a19ad42f665f471274ee75f328056dd55b17d
ms.sourcegitcommit: cd21b38eefdea2cdefb53e68e7a30b868e78dd6b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/22/2019
ms.locfileid: "66037097"
---
# <a name="synchronously-autoloaded-extensions"></a>Extensões carregadas automaticamente de modo sincrônico

Forma síncrona carregado automaticamente extensões têm um impacto negativo no desempenho do Visual Studio e devem ser convertidas para usar o autoload assíncrono em vez disso. A partir do Visual Studio 2019 Preview 2, os usuários são notificados quando uma extensão está sendo sincronicamente carregados automaticamente. A extensão carregará e funcionar normalmente.

![Aviso de compatibilidade de extensão](media/extension-compatibility-warning.png)

Os usuários podem:

- Clique em **Saiba mais** para acessar essa página de informações.

- Clique em **gerenciar o desempenho** para abrir o [caixa de diálogo Gerenciador de desempenho](#performance-manager-dialog) que mostra os problemas de desempenho com extensões e janelas de ferramentas.

- Clique em **não mostrar esta mensagem novamente** para ignorar a notificação. Escolher essa opção também impede que todas as notificações futuras de forma síncrona carregado automaticamente extensões. Os usuários continuarão a receber notificações sobre outros recursos do Visual Studio.

## <a name="performance-manager-dialog"></a>Caixa de diálogo Gerenciador de desempenho

![caixa de diálogo de Gerenciador de desempenho](media/performance-manager.png)

Todas as extensões de forma síncrona carregados todos os pacotes em todas as sessões de usuário aparecem na **APIs preteridas** guia.

* Os usuários podem clicar na **para obter mais informações sobre esse problema** para obter mais informações sobre as APIs obsoletas.
* Os usuários podem contate seus fornecedores de extensão para o andamento da migração.

Os autores de extensão podem encontrar instruções sobre como migrar pacotes para autoload assíncrono no [migrar para o AsyncPackage](https://github.com/Microsoft/VSSDK-Extensibility-Samples/tree/master/AsyncPackageMigration).

## <a name="specify-synchronous-autoload-settings-using-group-policy"></a>Especificar configurações de autoload síncrona usando diretiva de grupo

Iniciando o Visual Studio 2019 Update 1, por padrão, o autoload síncrona de blocos de instalação Visual Studio. Quando você habilita a política de grupo, você pode configurar o Visual Studio para permitir o autoload síncrona em computadores individuais. Para fazer isso, defina uma política baseada no Registro na seguinte chave:

**HKEY_LOCAL_MACHINE\SOFTWARE\Policies\Microsoft\VisualStudio\SynchronousAutoload**

Entrada = **permitido**

Valor = (DWORD)
* **0** autoload síncrona não é permitido
* **1** é síncrona autoload permitido

Para obter mais informações sobre as configurações de autoload síncrona na atualização 1 do Visual Studio de 2019, consulte o [comportamento síncrono de Autoload](https://aka.ms/AA52xzw) página.
