---
title: Switches de linha de comando Devenv para desenvolvimento de pacotes VS | Microsoft Docs
ms.date: 12/10/2018
ms.topic: conceptual
helpviewer_keywords:
- /Setup command line switch
- /ResetSkipPkgs command line switch
- /RootSuffix command line switch
- /SafeMode command line switch
- /Splash command line switch
- command-line switches
- registry, Visual Studio SDK
- command line, switches
- Visual Studio SDK, command-line switches
ms.assetid: d65d2c04-dd84-42b0-b956-555b11f5a645
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ad3a5125a730b9230959bbf9342b4c0a4823c4d3
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80712186"
---
# <a name="devenv-command-line-switches-for-vspackage-development"></a>Opções de linha de comando do Devenv para desenvolvimento de VSPackage

O Visual Studio permite que os desenvolvedores automatizem tarefas da linha de comando ao executar `devenv.exe`, o arquivo que inicia o Visual Studio IDE.

 As tarefas incluem:

- Implantação de aplicativos em configurações pré-projetadas de fora do IDE.

- Construção automática de projetos usando configurações de compilação predefinidas ou configurações de depuração.

- Carregando o IDE em configurações específicas, tudo de fora do IDE. Você também pode personalizar o IDE no lançamento.

## <a name="guidelines-for-switches"></a>Diretrizes para switches

A documentação do Visual `devenv` Studio descreve os switches de linha de comando de nível de usuário. Para obter mais informações, consulte [os switches de linha de comando Devenv](../ide/reference/devenv-command-line-switches.md). A `devenv` ferramenta também suporta switches adicionais de linha de comando que são úteis com desenvolvimento, implantação e depuração do VSPackage.

| Interruptor de linha de comando | Descrição |
|---------------------| - |
| `/ResetSkipPkgs` | Limpa todas as opções de carregamento de pular que foram adicionadas pelos usuários que querem evitar o carregamento de VSPackages problemáticos e, em seguida, inicia o Visual Studio. A presença de uma tag SkipLoading desativa o carregamento de um VSPackage. A compensação da tag reativa o carregamento do VSPackage.<br /><br /> Esta opção não aceita nenhum argumento. |
| `/RootSuffix` | Inicia o Visual Studio usando um local alternativo. O comando a seguir é executado pelo atalho criado pelo instalador visual studio SDK:<br /><br /> `devenv /RootSuffix exp`<br /><br /> Neste caso, `exp` identifica um local com um sufixo `10.0Exp` específico `10.0`(por exemplo, em vez de ). A instância experimental permite depurar um VSPackage separadamente da instância do Visual Studio que você está usando para escrever código.<br /><br /> Este switch pode pegar qualquer string que identifique um local que você criou usando VSRegEx.exe. Para obter mais informações, consulte [A Instância Experimental](../extensibility/the-experimental-instance.md). |
| `/SafeMode` | Lança o Visual Studio em modo seguro, carregando apenas o IDE padrão e os serviços. O `/SafeMode` switch impede que todos os VSPackages de terceiros seja carregado quando o Visual Studio for iniciado, garantindo a execução estável.<br /><br /> Esta opção não aceita nenhum argumento. |
| `/Setup` | Força o Visual Studio a mesclar metadados de recursos que descrevem menus, barras de ferramentas e grupos de comando de todos os VSPackages disponíveis. Você só pode executar este comando como um administrador. <br /><br /> Esta opção não aceita nenhum argumento. O comando `devenv /Setup` geralmente é fornecido como a última etapa do processo de instalação. O uso `/Setup` do interruptor não inicia o IDE.|
| `/Splash` | Mostra a tela de respingo do Visual Studio, como de costume, e, em seguida, mostra uma caixa de mensagem antes de mostrar o IDE principal. A caixa de mensagens permite estudar a tela de respingo (por exemplo, para verificar um ícone de produto VSPackage).<br /><br /> Esta opção não aceita nenhum argumento. |

## <a name="see-also"></a>Confira também

- [Adicionar interruptores de linha de comando](../extensibility/adding-command-line-switches.md)
- [Opções de linha de comando do Devenv](../ide/reference/devenv-command-line-switches.md)
