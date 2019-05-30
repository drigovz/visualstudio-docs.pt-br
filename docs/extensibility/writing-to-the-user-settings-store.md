---
title: Gravando o Store de configurações do usuário | Microsoft Docs
ms.date: 05/23/2019
ms.topic: conceptual
ms.assetid: efd27f00-7fe5-45f8-9b97-371af732be97
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 44380a03b87318be0fdf746c75eff8988ac68267
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66318477"
---
# <a name="writing-to-the-user-settings-store"></a>Gravando no repositório de configurações do usuário
Configurações de usuário são graváveis como aquelas na **Ferramentas / opções** caixa de diálogo, janelas Propriedades e determinadas outras caixas de diálogo. Extensões do Visual Studio podem usar estes para armazenar pequenas quantidades de dados. Este passo a passo mostra como adicionar o bloco de notas para o Visual Studio como uma ferramenta externa, leitura e gravação para o repositório de configurações do usuário.

## <a name="writing-to-the-user-settings-store"></a>Gravando no repositório de configurações do usuário

1. Crie um projeto VSIX chamado UserSettingsStoreExtension e, em seguida, adicione um comando personalizado chamado UserSettingsStoreCommand. Para obter mais informações sobre como criar um comando personalizado, consulte [criando uma extensão com um comando de Menu](../extensibility/creating-an-extension-with-a-menu-command.md)

2. No UserSettingsStoreCommand.cs, adicione as seguintes instruções using:

    ```csharp
    using System.Collections.Generic;
    using Microsoft.VisualStudio.Settings;
    using Microsoft.VisualStudio.Shell.Settings;
    ```

3. No MenuItemCallback, exclua o corpo do método e obter o usuário armazenam as configurações, da seguinte maneira:

    ```csharp
    private void MenuItemCallback(object sender, EventArgs e)
    {
        SettingsManager settingsManager = new ShellSettingsManager(ServiceProvider);
        WritableSettingsStore userSettingsStore = settingsManager.GetWritableSettingsStore(SettingsScope.UserSettings);
    }
    ```

4. Agora, descubra se o bloco de notas já está definido como uma ferramenta externa. Você precisa iterar por todas as ferramentas externas para determinar se a configuração ToolCmd é "Notepad", da seguinte maneira:

    ```csharp
    private void MenuItemCallback(object sender, EventArgs e)
    {
        SettingsManager settingsManager = new ShellSettingsManager(ServiceProvider);
        WritableSettingsStore userSettingsStore = settingsManager.GetWritableSettingsStore(SettingsScope.UserSettings);

        // Find out whether Notepad is already an External Tool.
        int toolCount = userSettingsStore.GetInt32("External Tools", "ToolNumKeys");
        bool hasNotepad = false;
        CompareInfo Compare = CultureInfo.InvariantCulture.CompareInfo;
        for (int i = 0; i < toolCount; i++)
        {
            if (Compare.IndexOf(userSettingsStore.GetString("External Tools", "ToolCmd" + i), "Notepad", CompareOptions.IgnoreCase) >= 0)
            {
                hasNotepad = true;
                break;
            }
        }
    }

    ```

5. Se o bloco de notas não foi definido como uma ferramenta externa, defina-o da seguinte maneira:

    ```vb
    private void MenuItemCallback(object sender, EventArgs e)
    {
        SettingsManager settingsManager = new ShellSettingsManager(ServiceProvider);
        WritableSettingsStore userSettingsStore = settingsManager.GetWritableSettingsStore(SettingsScope.UserSettings);

        // Find out whether Notepad is already installed.
        int toolCount = userSettingsStore.GetInt32("External Tools", "ToolNumKeys");
        bool hasNotepad = false;
        CompareInfo Compare = CultureInfo.InvariantCulture.CompareInfo;
        for (int i = 0; i < toolCount; i++)
        {
            if (Compare.IndexOf(userSettingsStore.GetString("External Tools", "ToolCmd" + i), "Notepad", CompareOptions.IgnoreCase) >= 0)
            {
                hasNotepad = true;
                break;
            }
        }

        string message = (hasNotepad) ? "Notepad already installed" : "Installing Notepad";
         if (!hasNotepad)
        {
            userSettingsStore.SetString("External Tools", "ToolTitle" + toolCount, "&Notepad");
            userSettingsStore.SetString("External Tools", "ToolCmd" + toolCount, "C:\\Windows\\notepad.exe");
            userSettingsStore.SetString("External Tools", "ToolArg" + toolCount, "");
            userSettingsStore.SetString("External Tools", "ToolDir" + toolCount, "$(ProjectDir)");
            userSettingsStore.SetString("External Tools", "ToolSourceKey" + toolCount, "");
            userSettingsStore.SetUInt32("External Tools", "ToolOpt" + toolCount, 0x00000011);

            userSettingsStore.SetInt32("External Tools", "ToolNumKeys", toolCount + 1);
        }
    }
    ```

6. Teste o código. Lembre-se de que ele adiciona o bloco de notas como uma ferramenta externa, portanto, você deve reverter o registro antes de executá-lo uma segunda vez.

7. Compilar o código e iniciar a depuração.

8. Sobre o **ferramentas** menu, clique em **UserSettingsStoreCommand invocar**. Isso adicionará o bloco de notas para o **ferramentas** menu.

9. Agora você deve ver o bloco de notas no menu Ferramentas / opções de menu e clicando em **bloco de notas** deve abrir uma instância do bloco de notas.