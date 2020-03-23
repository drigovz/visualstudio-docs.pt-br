---
title: Gerenciar configurações de aplicativo (.NET)
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- msvse_settingsdesigner.err.nameblank
helpviewer_keywords:
- application settings [Visual Studio]
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8d792a6147795f81211203fc442539371f3caa91
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75593701"
---
# <a name="manage-application-settings-net"></a>Gerenciar configurações de aplicativo (.NET)

As configurações de aplicativo permitem armazenar informações do aplicativo dinamicamente. As configurações permitem que você armazene informações no computador cliente que não devem ser incluídas no código do aplicativo (por exemplo, uma seqüência de conexão), preferências do usuário e outras informações que você precisa no tempo de execução.

As configurações de aplicativo substituem as propriedades dinâmicas usadas em versões anteriores do Visual Studio.

Cada configuração de aplicativo deve ter um nome exclusivo. O nome pode ser qualquer combinação de letras, números ou sublinhado, que não comece com número e que não pode conter espaços. O nome é alterado por meio da propriedade `Name`.

As configurações de aplicativo são armazenadas como qualquer tipo de dados que pode ser serializado para XML ou que tem um `TypeConverter` que implementa `ToString`/`FromString`. Os tipos mais comuns são `String`, `Integer` e `Boolean`, mas você também pode armazenar valores como <xref:System.Drawing.Color>, <xref:System.Object> ou como uma cadeia de conexão.

As configurações de aplicativo também contêm um valor. O valor é definido com a propriedade **Valor** e deve corresponder ao tipo de dados da configuração.

Além disso, as configurações de aplicativo podem ser associadas a uma propriedade de um formulário ou controle em tempo de design.

Há dois tipos de configurações de aplicativo, com base no escopo:

- Configurações de escopo do aplicativo podem ser usadas para informações como uma URL para um serviço Web ou uma cadeia de conexão de banco de dados. Esses valores são associados ao aplicativo. Portanto, os usuários não podem alterá-los em tempo de execução.

- Configurações de escopo do usuário podem ser usadas para informações, como persistir a última posição de um formulário ou uma preferência de fonte. Os usuários podem alterar esses valores em tempo de execução.

Você pode alterar o tipo de uma configuração usando a propriedade **Escopo**.

O sistema do projeto armazena configurações de aplicativo em dois arquivos XML:

- um arquivo *app.config,* que é criado na hora do design quando você cria a primeira configuração do aplicativo

- um arquivo *user.config,* que é criado no tempo de execução quando o usuário que executa o aplicativo altera o valor de qualquer configuração do usuário.

Observe que as alterações nas configurações do usuário não são gravadas em disco, a menos que o aplicativo especificamente chame um método para fazer isso.

## <a name="create-application-settings-at-design-time"></a>Criar configurações de aplicativo no tempo de design

Em tempo de design, você pode criar configurações de aplicativo de duas maneiras: usando a página **Configurações** do **Designer de Projeto** ou usando a janela **Propriedades** de um formulário ou controle, que permite que você associe uma configuração a uma propriedade.

Quando você cria uma configuração com escopo de aplicativo (por exemplo, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] uma seqüência de conexão `<applicationSettings>` de banco de dados ou uma referência aos recursos do servidor), salva-a no *app.config* com a tag. (As cadeias de conexão são salvas sob a marca `<connectionStrings>`.)

Quando você cria uma configuração com escopo do usuário (por exemplo, fonte padrão, página inicial ou tamanho da janela), [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] salva-a no *app.config* com a `<userSettings>` tag.

> [!IMPORTANT]
> Ao armazenar strings de conexão em *app.config,* você deve tomar precauções para evitar revelar informações confidenciais, como senhas ou caminhos do servidor, na seqüência de conexões.
>
> Se você obtiver as informações de cadeia de conexão de uma fonte externa, como um usuário fornecendo uma ID de usuário e senha, deverá ter cuidado para garantir que os valores usados para construir a cadeia de conexão não contêm parâmetros de cadeia de conexão adicionais que alteram o comportamento da conexão.
>
> Considere usar o recurso Configuração Protegida para criptografar informações confidenciais no arquivo de configuração. Para obter mais informações, confira [Proteger informações de conexão](/dotnet/framework/data/adonet/protecting-connection-information).

> [!NOTE]
> Como não há nenhum modelo de arquivo de configuração para bibliotecas de classes, as configurações de aplicativo não se aplicam a projetos de biblioteca de classes. A exceção é um projeto de DLL das Ferramentas do Visual Studio para Office, que pode ter um arquivo de configuração.

## <a name="use-customized-settings-files"></a>Usar arquivos de configurações personalizadas

Você pode adicionar arquivos de configurações personalizadas ao seu projeto para um gerenciamento conveniente de grupos de configurações. As configurações contidas em um único arquivo são carregadas e salvas como uma unidade. Armazenar as configurações em arquivos separados para grupos usados com frequência e usados raramente pode economizar tempo ao carregar e salvar as configurações.

Por exemplo, você pode adicionar um arquivo como *SpecialSettings.settings* ao seu projeto. Embora a classe `SpecialSettings` não seja exposta no namespace `My`, **Exibir Código** pode ler o arquivo de configurações personalizadas que contém `Partial Class SpecialSettings`.

O **Designer de configurações** pesquisa primeiro o arquivo *Configurações.configurações* que o sistema de projeto cria; este arquivo é o arquivo padrão que o **Project Designer** exibe na guia *Configurações.configurações está* localizado na pasta Meu *projeto* para [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] projetos e na pasta *Propriedades* para [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] projetos. **Settings** Em seguida, o **Project Designer** procura outros arquivos de configurações na pasta raiz do projeto. Portanto, você deve colocar o arquivo de configurações personalizado lá. Se você adicionar um arquivo *.settings* em outro lugar do projeto, o **Project Designer** não poderá localizá-lo.

## <a name="access-or-change-application-settings-at-run-time-in-visual-basic"></a>Acessar ou alterar as configurações de aplicativo no tempo de execução em Visual Basic

Em projetos do Visual Basic, você pode acessar as configurações de aplicativo no tempo de execução usando o objeto `My.Settings`. Na página **Configurações**, clique no botão **Exibir código** para exibir o arquivo *Settings.vb*. *Settings.vb* define `Settings` a classe, que permite lidar com esses <xref:System.Configuration.ApplicationSettingsBase.SettingChanging>eventos <xref:System.Configuration.ApplicationSettingsBase.PropertyChanged> <xref:System.Configuration.ApplicationSettingsBase.SettingsLoaded>na <xref:System.Configuration.ApplicationSettingsBase.SettingsSaving>classe de configurações: , , e . Observe que a classe `Settings` no *Settings.vb* é uma classe parcial que mostra apenas o código de propriedade do usuário, não toda a classe gerada. Para obter mais informações sobre como acessar as configurações de aplicativo usando o objeto `My.Settings`, confira [Acessar configurações de aplicativo (.NET Framework)](/dotnet/visual-basic/developing-apps/programming/app-settings/accessing-application-settings).

Os valores de qualquer configuração com escopo do usuário que o usuário altera no tempo de execução (por exemplo, a posição de um formulário) são armazenados em um arquivo *user.config.* Observe que os valores padrão ainda estão salvos em *app.config*.

Se as configurações no escopo do usuário forem alteradas durante o tempo de execução, por exemplo, no teste do aplicativo e você desejar redefinir essas configurações para seus valores padrão, clique no botão **Sincronizar**.

Recomendamos fortemente que `My.Settings` você use o objeto e o arquivo padrão *.settings* para acessar as configurações. Isso ocorre porque você pode usar o **Designer de Configurações** para atribuir propriedades às configurações e, além disso, as configurações do usuário são salvas automaticamente antes do desligamento do aplicativo. No entanto, seu aplicativo do Visual Basic pode acessar as configurações diretamente. Nesse caso, você tem `MySettings` que acessar a classe e usar um arquivo *personalizado .settings* na raiz do projeto. Você deve salvar as configurações do usuário antes de encerrar o aplicativo, como você faria para um aplicativo C#. Isso é descrito na próxima seção.

<!-- markdownlint-disable MD003 MD020 -->
## <a name="access-or-change-application-settings-at-run-time-in-c"></a>Acessar ou alterar as configurações de aplicativo no tempo de execução em C#
<!-- markdownlint-enable MD003 MD020 -->

Em linguagens diferentes do Visual Basic, como C#, você deve acessar a classe `Settings` diretamente, conforme mostrado no exemplo [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] a seguir.

```csharp
Properties.Settings.Default.FirstUserSetting = "abc";
```

Você deve chamar explicitamente o método `Save` dessa classe wrapper para persistir as configurações do usuário. Geralmente isso é feito no manipulador de eventos `Closing` do formulário principal. O exemplo C# a seguir mostra uma chamada para o método `Save`.

```csharp
Properties.Settings.Default.Save();
```

Para obter informações gerais sobre como `Settings` acessar as configurações do aplicativo através da classe, consulte [visão geral das configurações do aplicativo (.NET Framework)](/dotnet/framework/winforms/advanced/application-settings-overview). Para obter informações sobre como fazer a iteração por meio das configurações, consulte esta [postagem no fórum](https://social.msdn.microsoft.com/Forums/vstudio/40fbb470-f1e8-4a02-a4a0-9f62b54d0fc4/is-this-possible-propertiessettingsdefault?forum=csharpgeneral).

## <a name="see-also"></a>Confira também

- [Acessar configurações de aplicativo (.NET Framework)](/dotnet/visual-basic/developing-apps/programming/app-settings/accessing-application-settings)
