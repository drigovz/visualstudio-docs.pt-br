---
title: 'Como: Salvar e editar cadeias de conexão'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: f8ef3a2c-029c-423b-9d9e-a4f1add4f640
author: gewarren
ms.author: gewarren
manager: jillfra
ms.prod: visual-studio-dev15
ms.workload:
- data-storage
ms.openlocfilehash: 60253ada78391c48543e81093136da15e1446f91
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: pt-BR
ms.lasthandoff: 01/25/2019
ms.locfileid: "55000413"
---
# <a name="how-to-save-and-edit-connection-strings"></a>Como: Salvar e editar cadeias de conexão
Cadeias de caracteres de Conexão em aplicativos do Visual Studio são salvas no arquivo de configuração do aplicativo (também conhecido como configurações de aplicativo) ou codificadas diretamente no seu aplicativo. Salvar cadeias de conexão no arquivo de configuração do aplicativo simplifica a tarefa de realizar a manutenção de seu aplicativo. Se a cadeia de conexão precisar ser alterada, você poderá atualizá-la no arquivo de configurações do aplicativo (em vez de alterá-la no código-fonte e recompilar o aplicativo).

O armazenamento das informações confidenciais (tal como a senha) dentro da cadeia de conexão pode afetar a segurança do aplicativo. Cadeias de conexão salvas no arquivo de configuração do aplicativo não são criptografadas nem ofuscadas, de modo que talvez seja possível que alguém acesse o arquivo e exiba seu conteúdo. O uso da segurança integrada do Windows é uma maneira mais segura de controlar o acesso a um banco de dados.

Se você optar por não usar a segurança integrada do Windows e seu banco de dados exigir um nome de usuário e uma senha, você poderá omiti-los da cadeia de conexão, mas seu aplicativo precisará fornecer essas informações para se conectar com êxito ao banco de dados. Por exemplo, você pode criar uma caixa de diálogo que solicita ao usuário essas informações e compila dinamicamente a cadeia de conexão no tempo de execução. A segurança ainda pode ser um problema se as informações forem interceptadas no caminho para o banco de dados.
Para obter mais informações, confira [Protegendo informações de conexão](/dotnet/framework/data/adonet/protecting-connection-information).

## <a name="to-save-a-connection-string-from-within-the-data-source-configuration-wizard"></a>Para salvar uma cadeia de conexão de dentro do Assistente de configuração de fonte de dados
No **Data Source Configuration Wizard**, selecione a opção para salvar a conexão na **salvar a cadeia de Conexão no arquivo de configuração de aplicativo** página.

## <a name="to-save-a-connection-string-directly-into-application-settings"></a>Para salvar uma cadeia de conexão diretamente nas configurações do aplicativo
1. No **Gerenciador de Soluções**, clique duas vezes no ícone **Meu Projeto** (Visual Basic) ou no ícone **Propriedades** (C#) para abrir o **Designer de Projeto**.
1. Selecione a guia **Configurações**.
1. Insira um **Nome** para a cadeia de conexão. Consulte esse nome ao acessar a cadeia de conexão no código.
1. Configure o **Tipo** como (**Cadeia de conexão**).
1. Mantenha o **Escopo** configurado como **Aplicativo**.
1. Digite sua cadeia de caracteres de conexão na **valor** campo, ou clique no **reticências** botão (...) na **valor** campo para abrir o **depropriedadesdeConexão** caixa de diálogo para compilar sua cadeia de conexão.

## <a name="edit-connection-strings-stored-in-application-settings"></a>Editar cadeias de caracteres de conexão armazenadas nas configurações do aplicativo
Você pode modificar as informações da conexão que são salvas nas configurações do aplicativo usando o **Designer de Projeto**.

### <a name="to-edit-a-connection-string-stored-in-application-settings"></a>Para editar uma cadeia de conexão nas configurações do aplicativo
1. No **Gerenciador de Soluções**, clique duas vezes no ícone **Meu Projeto** (Visual Basic) ou no ícone **Propriedades** (C#) para abrir o **Designer de Projeto**.
1. Selecione a guia **Configurações**.
1. Localize a conexão que você deseja editar e selecione o texto na **valor** campo.
1. Edite a cadeia de conexão na **valor** campo, ou clique no **reticências** botão (...) na **valor** campo para editar sua conexão com o **Conexão Propriedades** caixa de diálogo.

## <a name="edit-connection-strings-for-datasets"></a>Editar cadeias de caracteres de conexão para conjuntos de dados
Você pode modificar as informações de conexão para cada TableAdapter em um conjunto de dados.

### <a name="to-edit-a-connection-string-for-a-tableadapter-in-a-dataset"></a>Para editar uma cadeia de caracteres de conexão para um TableAdapter em um conjunto de dados
1. Na **Gerenciador de soluções**, clique duas vezes no conjunto de dados (**. xsd** arquivo) que tem a conexão que você deseja editar.
1. Selecione o **TableAdapter** ou consulta que tenha a conexão que você deseja editar.
1. No **propriedades** janela, expanda o **nó Conexão**.
1. Para modificar rapidamente a cadeia de caracteres de conexão, edite a **ConnectionString** propriedade, ou clique na seta para baixo na **Conexão** propriedade e escolha **nova Conexão**.

## <a name="security"></a>Segurança
O armazenamento das informações confidenciais (tal como uma senha) dentro da cadeia de conexão pode afetar a segurança do aplicativo. O uso da segurança integrada do Windows é uma maneira mais segura de controlar o acesso a um banco de dados.
Para obter mais informações, confira [Protegendo informações de conexão](/dotnet/framework/data/adonet/protecting-connection-information).

## <a name="see-also"></a>Consulte também

- [Adicionando conexões](../data-tools/add-new-connections.md)