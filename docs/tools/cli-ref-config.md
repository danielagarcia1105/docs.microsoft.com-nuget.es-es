---
title: Comando config de NuGet CLI
description: Referencia para el comando config de nuget.exe
author: karann-msft
ms.author: karann
manager: unnir
ms.date: 01/18/2018
ms.topic: reference
ms.openlocfilehash: 9deab9fcca740ea99da61b7d54700a29c1813e88
ms.sourcegitcommit: 2a6d200012cdb4cbf5ab1264f12fecf9ae12d769
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/06/2018
ms.locfileid: "34818170"
---
# <a name="config-command-nuget-cli"></a><span data-ttu-id="e9f34-103">comando config (NuGet CLI)</span><span class="sxs-lookup"><span data-stu-id="e9f34-103">config command (NuGet CLI)</span></span>

<span data-ttu-id="e9f34-104">**Se aplica a:** todos los &bullet; **versiones compatibles**: todos los</span><span class="sxs-lookup"><span data-stu-id="e9f34-104">**Applies to:** all &bullet; **Supported versions**: all</span></span>

<span data-ttu-id="e9f34-105">Obtiene o establece los valores de configuración de NuGet.</span><span class="sxs-lookup"><span data-stu-id="e9f34-105">Gets or sets NuGet configuration values.</span></span> <span data-ttu-id="e9f34-106">Para uso adicionales, consulte [configuración de comportamiento de NuGet](../consume-packages/configuring-nuget-behavior.md).</span><span class="sxs-lookup"><span data-stu-id="e9f34-106">For additional usage, see [Configuring NuGet Behavior](../consume-packages/configuring-nuget-behavior.md).</span></span> <span data-ttu-id="e9f34-107">Para obtener información detallada sobre los nombres de clave permitidos, consulte la [referencia del archivo de configuración de NuGet](../reference/nuget-config-file.md).</span><span class="sxs-lookup"><span data-stu-id="e9f34-107">For details on allowable key names, refer to the [NuGet config file reference](../reference/nuget-config-file.md).</span></span>

## <a name="usage"></a><span data-ttu-id="e9f34-108">Uso</span><span class="sxs-lookup"><span data-stu-id="e9f34-108">Usage</span></span>

```cli
nuget config -Set <name>=[<value>] [<name>=<value> ...] [options]
nuget config -AsPath <name> [options]
```

<span data-ttu-id="e9f34-109">donde `<name>` y `<value>` especificar un par clave-valor que se establecerán en la configuración.</span><span class="sxs-lookup"><span data-stu-id="e9f34-109">where `<name>` and `<value>` specify a key-value pair to be set in the configuration.</span></span> <span data-ttu-id="e9f34-110">Puede especificar tantos pares según sea necesario.</span><span class="sxs-lookup"><span data-stu-id="e9f34-110">You can specify as many pairs as desired.</span></span> <span data-ttu-id="e9f34-111">Para quitar un valor, especifique el nombre y la `=` inicio de sesión, pero ningún valor.</span><span class="sxs-lookup"><span data-stu-id="e9f34-111">To remove a value, specify the name and the `=` sign but no value.</span></span>

<span data-ttu-id="e9f34-112">Para los nombres de clave permitidos, consulte la [referencia del archivo de configuración de NuGet](../reference/nuget-config-file.md).</span><span class="sxs-lookup"><span data-stu-id="e9f34-112">For allowable key names, see the [NuGet config file reference](../reference/nuget-config-file.md).</span></span>

<span data-ttu-id="e9f34-113">En NuGet 3.4 o superior, `<value>` puede usar [variables de entorno](cli-ref-environment-variables.md).</span><span class="sxs-lookup"><span data-stu-id="e9f34-113">In NuGet 3.4+, `<value>` can use [environment variables](cli-ref-environment-variables.md).</span></span>

## <a name="options"></a><span data-ttu-id="e9f34-114">Opciones</span><span class="sxs-lookup"><span data-stu-id="e9f34-114">Options</span></span>

| <span data-ttu-id="e9f34-115">Opción</span><span class="sxs-lookup"><span data-stu-id="e9f34-115">Option</span></span> | <span data-ttu-id="e9f34-116">Descripción</span><span class="sxs-lookup"><span data-stu-id="e9f34-116">Description</span></span> |
| --- | --- |
| <span data-ttu-id="e9f34-117">AsPath</span><span class="sxs-lookup"><span data-stu-id="e9f34-117">AsPath</span></span> | <span data-ttu-id="e9f34-118">Devuelve el valor de la configuración como una ruta de acceso, se omite cuando `-Set` se utiliza.</span><span class="sxs-lookup"><span data-stu-id="e9f34-118">Returns the config value as a path, ignored when `-Set` is used.</span></span> |
| <span data-ttu-id="e9f34-119">ConfigFile</span><span class="sxs-lookup"><span data-stu-id="e9f34-119">ConfigFile</span></span> | <span data-ttu-id="e9f34-120">El archivo de configuración de NuGet para modificar.</span><span class="sxs-lookup"><span data-stu-id="e9f34-120">The NuGet configuration file to modify.</span></span> <span data-ttu-id="e9f34-121">Si no se especifica, `%AppData%\NuGet\NuGet.Config` (Windows) o `~/.nuget/NuGet/NuGet.Config` (Mac o Linux) se utiliza.</span><span class="sxs-lookup"><span data-stu-id="e9f34-121">If not specified, `%AppData%\NuGet\NuGet.Config` (Windows) or `~/.nuget/NuGet/NuGet.Config` (Mac/Linux) is used.</span></span>|
| <span data-ttu-id="e9f34-122">ForceEnglishOutput</span><span class="sxs-lookup"><span data-stu-id="e9f34-122">ForceEnglishOutput</span></span> | <span data-ttu-id="e9f34-123">*(3.5 +)*  Fuerza nuget.exe ejecutándose con una referencia cultural invariable, basados en el inglés.</span><span class="sxs-lookup"><span data-stu-id="e9f34-123">*(3.5+)* Forces nuget.exe to run using an invariant, English-based culture.</span></span> |
| <span data-ttu-id="e9f34-124">Ayuda</span><span class="sxs-lookup"><span data-stu-id="e9f34-124">Help</span></span> | <span data-ttu-id="e9f34-125">Muestra información de ayuda para el comando.</span><span class="sxs-lookup"><span data-stu-id="e9f34-125">Displays help information for the command.</span></span> |
| <span data-ttu-id="e9f34-126">No interactivo</span><span class="sxs-lookup"><span data-stu-id="e9f34-126">NonInteractive</span></span> | <span data-ttu-id="e9f34-127">Suprime los mensajes para la entrada de usuario o confirmaciones.</span><span class="sxs-lookup"><span data-stu-id="e9f34-127">Suppresses prompts for user input or confirmations.</span></span> |
| <span data-ttu-id="e9f34-128">Nivel de detalle</span><span class="sxs-lookup"><span data-stu-id="e9f34-128">Verbosity</span></span> | <span data-ttu-id="e9f34-129">Especifica la cantidad de detalle que se muestra en la salida: *normal*, *quiet*, *detallada*.</span><span class="sxs-lookup"><span data-stu-id="e9f34-129">Specifies the amount of detail displayed in the output: *normal*, *quiet*, *detailed*.</span></span> |

<span data-ttu-id="e9f34-130">Consulte también [variables de entorno](cli-ref-environment-variables.md)</span><span class="sxs-lookup"><span data-stu-id="e9f34-130">Also see [Environment variables](cli-ref-environment-variables.md)</span></span>

### <a name="examples"></a><span data-ttu-id="e9f34-131">Ejemplos</span><span class="sxs-lookup"><span data-stu-id="e9f34-131">Examples</span></span>

```cli
nuget config -Set repositoryPath=c:\packages -configfile c:\my.config

nuget config -Set repositoryPath=

nuget config -Set repositoryPath=%PACKAGE_REPO% -configfile %ProgramData%\NuGet\NuGetDefaults.Config

nuget config -Set HTTP_PROXY=http://127.0.0.1 -set HTTP_PROXY.USER=domain\user
```