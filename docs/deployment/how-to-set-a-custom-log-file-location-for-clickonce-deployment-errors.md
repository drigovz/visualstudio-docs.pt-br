---
title: Definir local do arquivo de log personalizado (erros de implantação do ClickOnce)
description: Saiba mais sobre os arquivos de log de ativação que o ClickOnce mantém para todas as implantações, que documentam os erros de instalação e inicialização de uma implantação do ClickOnce.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- troubleshooting ClickOnce deployments
- ClickOnce deployment, troubleshooting
- ClickOnce deployment, error logging
ms.assetid: 77424414-7f0e-4b99-94bb-ea130de92d09
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 3d9c8ce481ab9ca99b7d456f53418641654369ad
ms.sourcegitcommit: 75bfdaab9a8b23a097c1e8538ed1cde404305974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/07/2020
ms.locfileid: "94351031"
---
# <a name="how-to-set-a-custom-log-file-location-for-clickonce-deployment-errors"></a>Como definir o local de um arquivo de log personalizado para erros de implantação do ClickOnce
[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] mantém arquivos de log de ativação para todas as implantações. Esses logs documentam os erros que pertencem à instalação e inicialização de uma [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] implantação. Por padrão, o [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] cria um arquivo de log para cada ativação de implantação. Ele armazena esses arquivos de log na pasta Temporary Internet Files. O arquivo de log para uma implantação é exibido para o usuário quando ocorre uma falha de ativação e o usuário clica em **detalhes** na caixa de diálogo de erro resultante.

 Você pode alterar esse comportamento para um cliente específico usando o editor do registro ( **regedit.exe** ) para definir um caminho de arquivo de log personalizado. Nesse caso, o [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] registra os êxitos e as falhas de ativação de todas as implantações em um único arquivo.

> [!CAUTION]
> Se o Editor do Registro for usado incorretamente, você pode causar sérios problemas que podem exigir que você reinstale o sistema operacional. Use o Editor do Registro por sua conta e risco.

> [!NOTE]
> Você precisará truncar ou excluir o arquivo de log ocasionalmente para impedir que ele fique muito grande.

 O procedimento a seguir descreve como definir um local de arquivo de log personalizado para um único cliente.

### <a name="to-set-a-custom-log-file-location"></a>Para definir um local de arquivo de log personalizado

1. Abra **Regedit.exe**.

2. Navegue até o nó `HKCU\Software\Classes\Software\Microsoft\Windows\CurrentVersion\Deployment` .

3. Defina o valor da cadeia de caracteres `LogFilePath` para o caminho completo e o nome do arquivo de seu local de log personalizado preferencial.

     Esse local deve estar em um diretório ao qual o usuário tenha acesso de gravação. Por exemplo, no Windows Vista, crie a seguinte estrutura de pastas e defina `LogFilePath` como *C:\Users \\ \<username> \Documents\Logs\ClickOnce\installation.log*.

## <a name="see-also"></a>Veja também
- [Solucionar problemas de implantações do ClickOnce](../deployment/troubleshooting-clickonce-deployments.md)