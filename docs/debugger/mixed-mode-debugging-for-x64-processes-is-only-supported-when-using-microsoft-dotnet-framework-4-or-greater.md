---
title: A depuração do modo misto para processos x64 só é suportada durante o uso do Microsoft.NET Framework 4 ou superior
description: As versões do .NET Framework anteriores à versão 4 não fornecem suporte à depuração de modo misto de processos do x64. Consulte este artigo para obter soluções alternativas.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.debug.error.interop_unsupported_x64
dev_langs:
- CSharp
- VB
- FSharp
- C++
ms.assetid: b7495655-54c0-4315-8422-43bf63b8c22e
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 92ec1022842e44f9f87069c48d4de3259dcf8e99
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99913198"
---
# <a name="mixed-mode-debugging-for-x64-processes-is-only-supported-when-using-microsoftnet-framework-4-or-greater"></a>A depuração do modo misto para processos x64 só é suportada durante o uso do Microsoft.NET Framework 4 ou superior
As versões do .NET Framework anteriores à versão 4 não fornecem suporte à depuração de modo misto de processos do x64. Isso significa que você não pode depurar de código gerenciado para código nativo, ou do código nativo para o código gerenciado.

### <a name="workarounds"></a>Soluções Alternativas

- Atualize seu projeto para usar o Microsoft .NET Framework 4 ou posterior.

     -ou-

     Depure seu código gerenciado e nativo em sessões separadas de depuração.

     -ou-

     Depure seu código misto como um processo de 32 bits, como descrito nos procedimentos a seguir.

### <a name="to-change-the-platform-to-32-bit-visual-basic-or-c"></a>Para alterar a plataforma para 32 bits (Visual Basic ou C#)

1. No **Gerenciador de Soluções**, clique com o botão direito do mouse no nó do seu projeto e clique em **Propriedades**.

2. Nas páginas de propriedades, clique na guia **Compilar** ou **Depurar**.

3. Clique em **Plataforma** e selecione x86 na lista de plataformas.

     Por padrão, os compiladores padrão do Visual Basic e do C# produzem código para ser executado em qualquer CPU. Em um computador de 64 bits, esses binários são executados como processos de 64 bits. Para executar em um processo de 32 bits, você deve escolher **Win32** e não **AnyCPU**.

### <a name="to-change-the-platform-to-32-bit-cc"></a>Para alterar a plataforma para 32 bits (C/C++)

1. No **Gerenciador de Soluções**, clique com o botão direito do mouse no nó do seu projeto e clique em **Propriedades**.

2. Nas páginas de propriedades, clique em **plataforma** e selecione Win32 na lista de plataformas.

### <a name="to-correct-this-error"></a>Para corrigir este erro

- Consulte [Configurando a depuração do SQL](/previous-versions/visualstudio/visual-studio-2010/s4sszxst(v=vs.100)).

## <a name="see-also"></a>Consulte também
- [Depurar aplicativos de 64 bits](../debugger/debug-64-bit-applications.md)