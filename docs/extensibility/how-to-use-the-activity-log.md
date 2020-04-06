---
title: 'Como: Usar o Registro de Atividades | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSPackages, debugging
- VSPackages, troubleshooting
ms.assetid: bb3d3322-0e5e-4dd5-b93a-24d5fbcd2ffd
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 64986be303370cf8c9048612ff3d44e82e96805a
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80710574"
---
# <a name="how-to-use-the-activity-log"></a>Como: Usar o registro de atividades
VsPackages podem gravar mensagens no registro de atividades. Este recurso é especialmente útil para depurar VSPackages em ambientes de varejo.

> [!TIP]
> O registro de atividades está sempre ligado. O Visual Studio mantém um buffer de rolamento das últimas 100 entradas, bem como as primeiras 10 entradas, que têm informações gerais de configuração.

## <a name="to-write-an-entry-to-the-activity-log"></a>Para escrever uma entrada no registro de atividades

1. Insira este <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A> código no método ou em qualquer outro método, exceto o construtor VSPackage:

    ```csharp
    IVsActivityLog log = GetService(typeof(SVsActivityLog)) as IVsActivityLog;
    if (log == null) return;

    int hr = log.LogEntry((UInt32)__ACTIVITYLOG_ENTRYTYPE.ALE_INFORMATION,
        this.ToString(),
        string.Format(CultureInfo.CurrentCulture,
        "Called for: {0}", this.ToString()));
    ```

     Este código <xref:Microsoft.VisualStudio.Shell.Interop.SVsActivityLog> recebe o serviço e <xref:Microsoft.VisualStudio.Shell.Interop.IVsActivityLog> lança-o para uma interface. <xref:Microsoft.VisualStudio.Shell.Interop.IVsActivityLog.LogEntry%2A>escreve uma entrada informacional no registro de atividades usando o contexto cultural atual.

2. Quando o VSPackage é carregado (geralmente quando um comando é invocado ou uma janela é aberta), o texto é gravado no registro de atividades.

## <a name="to-examine-the-activity-log"></a>Para examinar o registro de atividades

1. Execute o Visual Studio com o switch de linha de comando [/Log](../ide/reference/log-devenv-exe.md) para gravar ActivityLog.xml em disco durante a sessão.

2. Após fechar o Visual Studio, encontre o login de atividade na subpasta para dados do Visual Studio:

   <em> *%AppData%</em>\Microsoft\VisualStudio\\\<versão>\ActivityLog.xml*.

3. Abra o registro de atividades com qualquer editor de texto. Aqui está uma entrada típica:

   ```
   Called for: Company.MyApp.MyAppPackage ...
   ```

## <a name="robust-programming"></a>Programação robusta

Como o registro de atividades é um serviço, o registro de atividades não está disponível no construtor VSPackage.

Você deve obter o registro de atividades pouco antes de escrever para ele. Não faça cache ou salve o registro de atividades para uso futuro.

## <a name="see-also"></a>Confira também

- [/Log (devenv.exe)](../ide/reference/log-devenv-exe.md)
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsActivityLog>
- <xref:Microsoft.VisualStudio.Shell.Interop.__ACTIVITYLOG_ENTRYTYPE>
- [Solucionando problemas de VSPackages](../extensibility/troubleshooting-vspackages.md)
- [VSPackages](../extensibility/internals/vspackages.md)
