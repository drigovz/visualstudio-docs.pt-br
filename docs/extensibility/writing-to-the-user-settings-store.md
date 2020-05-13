---
title: Escrevendo para a Loja de Configurações do Usuário | Microsoft Docs
ms.date: 05/23/2019
ms.topic: conceptual
ms.assetid: efd27f00-7fe5-45f8-9b97-371af732be97
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 2bed721cc084042c3ebe57639af28b7e9f13d206
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80740367"
---
# <a name="writing-to-the-user-settings-store"></a>Gravando no repositório de configurações do usuário
As configurações do usuário são configurações graváveis como as da caixa de diálogo **Ferramentas / Opções,** janelas de propriedades e certas outras caixas de diálogo. As extensões do Visual Studio podem usá-las para armazenar pequenas quantidades de dados. Este passo a passo mostra como adicionar o Bloco de Notas ao Visual Studio como uma ferramenta externa, lendo e escrevendo na loja de configurações do usuário.

## <a name="writing-to-the-user-settings-store"></a>Gravando no repositório de configurações do usuário

1. Crie um projeto VSIX chamado UserSettingsStoreExtension e adicione um comando personalizado chamado UserSettingsStoreCommand. Para obter mais informações sobre como criar um comando personalizado, consulte [Criando uma extensão com um comando menu](../extensibility/creating-an-extension-with-a-menu-command.md)

2. Em UserSettingsStoreCommand.cs, adicione as seguintes diretivas usando:

    ```csharp
    using System.Collections.Generic;
    using Microsoft.VisualStudio.Settings;
    using Microsoft.VisualStudio.Shell.Settings;
    ```

3. Em MenuItemCallback, exclua o corpo do método e obtenha a loja de configurações do usuário, da seguinte forma:

    ```csharp
    private void MenuItemCallback(object sender, EventArgs e)
    {
        SettingsManager settingsManager = new ShellSettingsManager(ServiceProvider);
        WritableSettingsStore userSettingsStore = settingsManager.GetWritableSettingsStore(SettingsScope.UserSettings);
    }
    ```

4. Agora descubra se o Bloco de Notas já está definido como uma ferramenta externa. Você precisa iterar através de todas as ferramentas externas para determinar se a configuração ToolCmd é "Bloco de notas", da seguinte forma:

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

5. Se o Bloco de Notas não tiver sido definido como uma ferramenta externa, defina-o da seguinte forma:

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

6. Teste o código. Lembre-se de que ele adiciona o Bloco de Notas como uma ferramenta externa, então você deve reverter o registro antes de executá-lo uma segunda vez.

7. Construa o código e comece a depurar.

8. No menu **Ferramentas,** clique **em Invocar UserSettingsStoreCommand**. Isso adicionará o Bloco de Notas ao menu **Ferramentas.**

9. Agora você deve ver o Bloco de Notas no menu Ferramentas / Opções, e clicar no **bloco de notas** deve trazer uma instância do Bloco de Notas.
