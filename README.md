# RE-Compactos

A library to transparently compact file system in Windows; to save disk space.

Features:

- Compact OS files
- Compact custom files and folders (e.g Steam games)
- Automatic optimal algorithm selection (LZX, Xpress, Xpress4K, ...)
- Uncompact/Revert to original state
- Advanced custom file and folder exclution
- Thread-safe

# Why compact OS files. isn't a bad idea?

When Windows boots. It does not load all the files in the system-drive. This is a problem when you have a lot of files in the OS partition. This library will compact the OS files and will make the boot faster. and save your disk space.

// TODO

## Performance

// TODO: benchmark image

# Usage

## Check status

```csharp
using System;
using ReEnhancer.OSCompact;

var compactor = new OSCompactManager();
var status = await compactor.GetStatus();
Console.WriteLine($"Status: {status}");
// Would output: Status: OS=NotCompacted

```

## Get optimal algorithm for current machine

```csharp
using System;
using ReEnhancer.OSCompact;

var compactor = new OSCompactManager();
var algorithm = await compactor.GetOptimalAlgorithm();
Console.WriteLine($"Algorithm: {algorithm}");
// Output: ShouldNotCompact or LZX or Xpress or Xpress4K

```

## Compact Windows OS

//TODO

## Compact custom folder

//TODO

## Advanced: custom exclution rule with

```csharp
using System;
using System.IO;
using System.Threading;
using ReEnhancer.OSCompact;

public class MyRuleset: IExclutionRule
{

        public void Initialize(CompactionContext context)
        {
            // Called once compaction process begins.
        }

        public bool Execute(CancellationToken cancellationToken, FileExclutionContext context)
        {
            if (context.File.Length > 4000)
            return true;

        }
}
```

```csharp
using System;
using ReEnhancer.OSCompact;

var compactor = new OSCompactManager();
compactor.ExclutionRule.Add(new MyRuleSet())

```

## Uncompact/Revert

//TODO

# FAQ

Q: Are there any GUIs for this library?

A: Yes, this library is built exclusively for [RE-Enhancer](). but can be used from any .NET project.

# License

RE-Compactos is licensed under the [GPLv3](/LICENSE)
