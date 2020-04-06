---
title: Usando a Loja de Configurações | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Settings Store, using
ms.assetid: 447ec08a-eca5-40b8-89b0-f98fdf3d39a4
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b3bbc09586f883e067e32f525a0331c1a9e253f5
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80698510"
---
# <a name="using-the-settings-store"></a>Usar o repositório de configurações
Existem dois tipos de configurações:

- Configurações de configuração, que são configurações somente de Visual Studio e VSPackage. O Visual Studio mescla configurações de todos os arquivos .pkgdef conhecidos nesta loja.

- Configurações do usuário, que são configurações graváveis, como aquelas exibidas em páginas na caixa de diálogo **Opções,** páginas de propriedade e certas outras caixas de diálogo. As extensões do Visual Studio podem usá-las para armazenamento local de pequenas quantidades de dados.

  Este passo a passo mostra como ler dados do armazenamento de configuração. Consulte [Escrever na Loja de Configurações do Usuário](../extensibility/writing-to-the-user-settings-store.md) para obter uma explicação de como escrever na loja de configurações do usuário.

## <a name="creating-the-example-project"></a>Criando o Projeto Exemplo
 Esta seção mostra como criar um projeto de extensão simples com um comando de menu para demonstração.

1. Toda extensão do Visual Studio começa com um projeto de implantação vsix que conterá os ativos de extensão. Crie [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] um projeto `SettingsStoreExtension`VSIX chamado . Você pode encontrar o modelo de projeto VSIX na caixa de diálogo **Novo Projeto** em **Visual C# / Extensibility**.

2. Agora adicione um modelo de item de comando personalizado chamado **SettingsStoreCommand**. Na **caixa de diálogo Adicionar novo item,** vá para **Visual C# / Extensibility** e selecione **Comando Personalizado**. No **campo Nome,** na parte inferior da janela, altere o nome do arquivo de comando para **SettingsStoreCommand.cs**. Para obter mais informações sobre como criar um comando personalizado, consulte [Criando uma extensão com um comando menu](../extensibility/creating-an-extension-with-a-menu-command.md)

## <a name="using-the-configuration-settings-store"></a>Usando o armazenamento de configurações
 Esta seção mostra como detectar e exibir configurações.

1. No arquivo SettingsStorageCommand.cs, adicione as seguintes diretivas usando:

   ```
   using System.Collections.Generic;
   using Microsoft.VisualStudio.Settings;
   using Microsoft.VisualStudio.Shell.Settings;
   using System.Windows.Forms;
   ```

2. Em `MenuItemCallback`, remova o corpo do método e adicione essas linhas obter as configurações de configuração armazenar:

   ```
   SettingsManager settingsManager = new ShellSettingsManager(ServiceProvider);
   SettingsStore configurationSettingsStore = settingsManager.GetReadOnlySettingsStore(SettingsScope.Configuration);
   ```

    O <xref:Microsoft.VisualStudio.Shell.Settings.ShellSettingsManager> é uma classe de <xref:Microsoft.VisualStudio.Shell.Interop.IVsSettingsManager> ajudante gerenciado sobre o serviço.

3. Agora descubra se as Ferramentas do Windows Phone estão instaladas. O código deve ser assim:

   ```
   private void MenuItemCallback(object sender, EventArgs e)
   {
       SettingsManager settingsManager = new ShellSettingsManager(ServiceProvider);
       SettingsStore configurationSettingsStore = settingsManager.GetReadOnlySettingsStore(SettingsScope.Configuration);
       bool arePhoneToolsInstalled = configurationSettingsStore.CollectionExists(@"InstalledProducts\Microsoft Windows Phone Developer Tools");
       string message = "Microsoft Windows Phone Developer Tools: " + arePhoneToolsInstalled;
       MessageBox.Show(message);
   }
   ```

4. Teste o código. Compile o projeto e comece a depuração.

5. Na instância experimental, no menu **Ferramentas,** clique em **Invocar ConfiguraçõesStoreCommand**.

    Você deve ver uma caixa de mensagens dizendo **Ferramentas de Desenvolvedor de Telefones Do Microsoft Windows:** seguida por **True** ou **False**.

   O Visual Studio mantém a loja de configurações no registro do sistema.

#### <a name="to-use-a-registry-editor-to-verify-configuration-settings"></a>Para usar um editor de registro para verificar configurações de configuração

1. Abra Regedit.exe.

2. Navegue até HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\14.0Exp_Config\Produtos\\Instalados .

    > [!NOTE]
    > Certifique-se de que está olhando para a chave que contém \14.0Exp_Config\ e não \14.0_Config\\. Quando você executa a instância experimental do Visual Studio, as configurações estão na colmeia de registro "14.0Exp_Config".

3. Expanda o nó \Produtos Instalados\. Se a mensagem nas etapas anteriores for ferramentas do **Desenvolvedor microsoft windows phone instaladas: True**, então \Produtos instalados\ deve conter um nó Microsoft Windows Phone Developer Tools. Se a mensagem for ferramentas do **Desenvolvedor microsoft windows phone instaladas: falsas**, então \Produtos instalados\ não deve conter um nó Microsoft Windows Phone Developer Tools.
