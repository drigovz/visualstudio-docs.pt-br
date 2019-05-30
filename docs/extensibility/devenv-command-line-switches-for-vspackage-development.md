---
title: Opções de linha de comando devenv para desenvolvimento de VSPackage | Microsoft Docs
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
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 289f31c503143dc2b992717483f4d8701414e09d
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66348049"
---
# <a name="devenv-command-line-switches-for-vspackage-development"></a>Opções de linha de comando devenv para desenvolvimento de VSPackage

O Visual Studio permite aos desenvolvedores automatizarem as tarefas da linha de comando ao executar `devenv.exe`, o arquivo que inicia o IDE do Visual Studio.

 As tarefas incluem:

- Implantando aplicativos em configurações predefinidas de fora do IDE.

- Compilando projetos usando a predefinição de configurações de build ou automaticamente configurações de depuração.

- Carregando o IDE em configurações específicas, tudo a partir de fora do IDE. Você também pode personalizar o IDE durante a inicialização.

## <a name="guidelines-for-switches"></a>Diretrizes para comutadores

Documentação do Visual Studio descreve o nível de usuário `devenv` de linha de comando. Para obter mais informações, consulte [opções de linha de comando do Devenv](../ide/reference/devenv-command-line-switches.md). O `devenv` ferramenta também dá suporte a opções de linha de comando adicionais que são úteis com desenvolvimento VSPackage, implantação e depuração.

| Opção de linha de comando | Descrição |
|---------------------| - |
| `/ResetSkipPkgs` | Limpa todas as opções de carregamento de ignorar que foram adicionadas por usuários que desejam evitar carregar VSPackages problemáticos e, em seguida, inicia o Visual Studio. A presença de uma marcação SkipLoading desabilita o carregamento de um VSPackage. Limpar a marcação habilita novamente o carregamento do VSPackage.<br /><br /> Esta opção não aceita nenhum argumento. |
| `/RootSuffix` | Inicia o Visual Studio por meio de um local alternativo. O comando a seguir é executado pelo atalho criado pelo instalador do SDK do Visual Studio:<br /><br /> `devenv /RootSuffix exp`<br /><br /> Nesse caso, `exp` identifica um local com um sufixo específico (por exemplo, `10.0Exp` em vez de `10.0`). A instância experimental permite que você depure um VSPackage separadamente da instância do Visual Studio que você está usando para escrever código.<br /><br /> Essa opção pode levar a qualquer cadeia de caracteres que identifica um local que você criou usando VSRegEx.exe. Para obter mais informações, consulte [a instância Experimental](../extensibility/the-experimental-instance.md). |
| `/SafeMode` | Visual Studio é iniciado no modo de segurança, carregando apenas o padrão IDE e serviços. O `/SafeMode` switch impede que todos os VSPackages de terceiros de carregamento quando o Visual Studio é iniciado, garantindo uma execução estável.<br /><br /> Esta opção não aceita nenhum argumento. |
| `/Setup` | Força o Visual Studio a mesclar os metadados de recursos que descrevem menus, barras de ferramentas e grupos de comando de todos os VSPackages disponíveis. Você só pode executar esse comando como administrador. <br /><br /> Esta opção não aceita nenhum argumento. O comando `devenv /Setup` geralmente é fornecido como a última etapa do processo de instalação. Usar o `/Setup` switch não inicie o IDE.|
| `/Splash` | Mostra a abertura do Visual Studio de tela, como de costume, e, em seguida, exibe uma mensagem de caixa antes de mostrar o IDE principal. A caixa de mensagem permite que você estude a tela inicial (por exemplo, para verificar se há um ícone de VSPackage do produto).<br /><br /> Esta opção não aceita nenhum argumento. |

## <a name="see-also"></a>Consulte também

- [Adicionar opções de linha de comando](../extensibility/adding-command-line-switches.md)
- [Opções de linha de comando do Devenv](../ide/reference/devenv-command-line-switches.md)