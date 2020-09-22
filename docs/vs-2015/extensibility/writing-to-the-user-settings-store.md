---
title: Gravando no repositório de configurações do usuário | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
ms.assetid: efd27f00-7fe5-45f8-9b97-371af732be97
caps.latest.revision: 4
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 764d9b81297c6bbefd1f5fdf7c77e4d514bb5045
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "90838614"
---
# <a name="writing-to-the-user-settings-store"></a>Gravando no repositório de configurações do usuário
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

As configurações de usuário são configurações graváveis, como aquelas na caixa de diálogo **ferramentas/opções** , janelas de propriedades e algumas outras caixas de diálogo. As extensões do Visual Studio podem usá-las para armazenar pequenas quantidades de dados. Este tutorial mostra como adicionar o bloco de notas ao Visual Studio como uma ferramenta externa, lendo e gravando no repositório de configurações do usuário.  
  
### <a name="backing-up-your-user-settings"></a>Fazendo backup de suas configurações de usuário  
  
1. Você deve ser capaz de redefinir as configurações de ferramentas externas para que possa depurar e repetir o procedimento. Para fazer isso, você deve salvar as configurações originais para que possa restaurá-las conforme necessário.  
  
2. Abra Regedit.exe.  
  
3. Navegue até HKEY_CURRENT_USER \Software\Microsoft\VisualStudio\14.0Exp\External Tools \\ .  
  
    > [!NOTE]
    > Verifique se você está olhando a chave que contém \14.0Exp\ e não \ 14,0 \\ . Quando você executa a instância experimental do Visual Studio, suas configurações de usuário estão no hive do registro "14.0 Exp".  
  
4. Clique com o botão direito do mouse na subchave \External Tools e clique em **Exportar**. Verifique se a **ramificação selecionada** está selecionada.  
  
5. Salve o arquivo. reg das ferramentas externas resultantes.  
  
6. Posteriormente, quando você quiser redefinir as configurações de ferramentas externas, selecione a chave HKEY_CURRENT_USER \Software\Microsoft\VisualStudio\14.0Exp\External Tools \ registro e clique em **excluir** no menu de contexto.  
  
7. Quando a caixa de diálogo **Confirmar exclusão de chave** for exibida, clique em **Sim**.  
  
8. Clique com o botão direito do mouse no arquivo. reg de ferramentas externas que você salvou anteriormente, clique em **abrir com**e, em seguida, clique em **Editor do registro**.  
  
## <a name="writing-to-the-user-settings-store"></a>Gravando no repositório de configurações do usuário  
  
1. Crie um projeto VSIX chamado UserSettingsStoreExtension e, em seguida, adicione um comando personalizado chamado UserSettingsStoreCommand. Para obter mais informações sobre como criar um comando personalizado, consulte [criando uma extensão com um comando de menu](../extensibility/creating-an-extension-with-a-menu-command.md)  
  
2. No UserSettingsStoreCommand.cs, adicione as seguintes instruções using:  
  
    ```csharp  
    using System.Collections.Generic;  
    using Microsoft.VisualStudio.Settings;  
    using Microsoft.VisualStudio.Shell.Settings;  
    ```  
  
3. No MenuItemCallback, exclua o corpo do método e obtenha o armazenamento de configurações do usuário, da seguinte maneira:  
  
    ```csharp  
    private void MenuItemCallback(object sender, EventArgs e)  
    {  
        SettingsManager settingsManager = new ShellSettingsManager(ServiceProvider);  
        WritableSettingsStore userSettingsStore = settingsManager.GetWritableSettingsStore(SettingsScope.UserSettings);  
    }  
    ```  
  
4. Agora descubra se o bloco de notas já está definido como uma ferramenta externa. Você precisa iterar em todas as ferramentas externas para determinar se a configuração ToolCmd é "notepad", da seguinte maneira:  
  
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
  
5. Se o bloco de notas não tiver sido definido como uma ferramenta externa, defina-o da seguinte maneira:  
  
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
  
7. Compile o código e inicie a depuração.  
  
8. No menu **ferramentas** , clique em **invocar UserSettingsStoreCommand**. Isso adicionará o bloco de notas ao menu **ferramentas** .  
  
9. Agora você deve ver o bloco de notas no menu ferramentas/opções e clicar em **bloco** de notas deve exibir uma instância do bloco de notas.
