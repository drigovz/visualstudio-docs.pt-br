---
title: Desenvolvimento colaborativo de soluções do Office
description: Saiba como vários desenvolvedores podem trabalhar em um projeto do Office da mesma maneira que colaboram em outros projetos do Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office applications [Office development in Visual Studio], collaborative development
- Office development in Visual Studio, collaboration
- source control [Office development in Visual Studio]
- collaborative development [Office development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: d30f28b3e97469bc9e0bf921438960206b4f89c0
ms.sourcegitcommit: ce85cff795df29e2bd773b4346cd718dccda5337
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/08/2020
ms.locfileid: "96845798"
---
# <a name="collaborative-development-of-office-solutions"></a>Desenvolvimento colaborativo de soluções do Office
  Vários desenvolvedores podem trabalhar em um projeto do Office da mesma maneira que colaboram em outros projetos do Visual Studio. O Visual Studio localiza corretamente a instalação do Microsoft Office em cada computador, mesmo se o Office estiver instalado em locais diferentes. No entanto, há algumas considerações importantes a serem observadas.

 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

## <a name="debug-properties-are-not-shared"></a>As propriedades de depuração não são compartilhadas
 As propriedades de depuração não são compartilhadas entre vários usuários sob controle do código-fonte. Os projetos Visual Basic e Visual C# armazenam as propriedades de depuração em um arquivo específico do usuário (*ProjectName*. vbproj. User ou *ProjectName*. csproj. User) e esse arquivo não está no controle do código-fonte. Se mais de uma pessoa estiver Depurando, cada pessoa deverá inserir as propriedades de depuração manualmente.

 Se o projeto estiver hospedado em um compartilhamento de rede em vez de no controle do código-fonte, algumas etapas adicionais deverão ser executadas para permitir que os desenvolvedores de colaboração Abram a solução e testem o assembly.

## <a name="source-control-requires-checking-out-all-files"></a>O controle do código-fonte requer a verificação de todos os arquivos
 Se você usar o controle do código-fonte para seus projetos, deverá fazer check-out de todos os arquivos em um arquivo de código em **Gerenciador de soluções** (como os arquivos de código *ThisDocument*, *ThisWorkbook* ou *ThisAddIn* ) sempre que alterar o arquivo de código, até mesmo os arquivos ocultos por padrão. Se você fizer check-out apenas do arquivo de código de nível superior, suas alterações poderão ser perdidas.

 Depois de fazer as alterações, verifique todos os arquivos novamente. Para obter mais informações sobre arquivos de código ocultos em projetos, consulte [projetos do Office no ambiente do Visual Studio](../vsto/office-projects-in-the-visual-studio-environment.md).

## <a name="security-for-informal-collaboration-on-a-network"></a>Segurança para colaboração informal em uma rede
 Para todas as soluções em nível de documento que estão em um local de rede (como \\ \\ *nomedoservidor* \\ *ShareName*), o local totalmente qualificado deve ser adicionado à lista de pastas confiáveis no aplicativo Microsoft Office com o qual você está trabalhando. Selecione a opção para incluir os subdiretórios na pasta principal ou especificamente Adicione depurar e criar pastas à lista de pastas confiáveis. Para obter mais informações sobre como fazer isso, consulte [conceder confiança a documentos](../vsto/granting-trust-to-documents.md).

 Os certificados temporários gerados automaticamente no momento da compilação não são protegidos por senhas. Os certificados contêm o nome de logon do desenvolvedor e outras informações pessoais. Se você implantar personalizações que são assinadas por certificados temporários, outras pessoas poderão acessar essas informações.

## <a name="see-also"></a>Confira também
- [Proteger soluções do Office](../vsto/securing-office-solutions.md)
- [Projetar e criar soluções do Office](../vsto/designing-and-creating-office-solutions.md)
- [Criar soluções do Office](../vsto/building-office-solutions.md)
