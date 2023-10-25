# Windows Device Recovery Tool update bypass

While the Windows Device Recovery Tool installer got unbroken back in mid-2023 again, it seems like WDRT itself cannot find the servers to check for updates properly. This means WDRT itself will refuse to run, unless of course you disable the update check which is easy since *there is a build-time option for it that microsoft chose not to make toggleable*.

## How to

1. Copy the WindowsDeviceRecoveryTool.exe to your documents or something.
2. Download [dnSpy](https://github.com/dnSpyEx/dnSpy).
3. Open the WDRT exe in dnSpy.
4. Navigate to `WindowsDeviceRecoveryTool` > `WindowsDeviceRecoveryTool.exe` > `Microsoft.WindowsDeviceRecoveryTool.ApplicationLogic` > `ApplicationBuildSettings` > `SkipApplicationUpdate`
5. In the view where something like "get { return false; }" is visible, right click to "Edit Method (C#)..."
6. Replace false with true
7. Click compile
8. Go to file -> save module and save the exe somewhere
9. Copy the saved exe over the old WDRT exe
10. Run it and it should now skip the update check

## Dear software vendors: forced update checks to run an offline app are fucking stupid

Please. Just don't.
