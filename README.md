<h1 align="center">MacApi.Dialogs</h1>
<p align="center">Simplified NSOpenPanel and NSSavePanel Delphi bridge using MacApi default units</p>
<p align="center"><b>Lily Stilson // 2019</b></p>
<hr>

## Usage
This unit is meant to be working with RAD Studio 10.3.2. Other remain untested, but probably will work too.</p>

### InvokeNSOpenPanel
Simplified NSOpenPanel creation.

```Pascal
function InvokeNSOpenPanel (const Title: String; const InitialDir: String; 
                            const Flags: String; const AllowedFileTypes: TArray<String>; 
                            var ADir: String): Boolean
```

- **Title** - NSOpenPanel Title
- **InitialDir** - Initial NSOpenPanel directory
- **Flags** - A string set of flags separated with space, that will enable or disable certain NSOpenPanel features
  - **multiple** - Enable multiple file selection
  - **others** - Enable file types other than **AllowedFileTypes** ones
  - **create** - Allow NSOpenPanel to create folders
  - **hidden** - Enable hidden directories
- **AllowedFileTypes** - An array of allowed file types for NSOpenPanel
- **ADir** - Returnable value of path to opened file / files


### InvokeNSSavePanel
Simplified NSSavePanel creation.

```Pascal
function InvokeNSSavePanel (const Title: String; const InitialDir: String; 
                            const Flags: String; const FileTypesDescription: TArray<String;
                            const AllowedFileTypes: TArray<String>; var ADir: String): Boolean
```

- **Title** - NSSavePanel Title
- **InitialDir** - Initial NSSavePanel directory
- **Flags** - A string set of flags separated with space, that will enable or disable certain NSSavePanel features
  - **others** - Enable file types other than **AllowedFileTypes** ones
  - **create** - Allow NSSavePanel to create folders
  - **hidden** - Enable hidden directories
- **FileTypesDescription** - An array of names of allowed file types for NSSavePanel
- **AllowedFileTypes** - An array of allowed file types for NSSavePanel
- **ADir** - Returnable value of path to saved file


### InvokeNSOpenDirPanel
Simplified NSOpenPanel creation in Directory selection mode.

```Pascal
function InvokeNSOpenDirPanel(const Title: String; const InitialDir: String; 
                              const Flags: String; var ADir: String): Boolean
```

- **Title** - NSOpenPanel Title
- **InitialDir** - Initial NSOpenPanel directory
- **Flags** - A string set of flags separated with space, that will enable or disable certain NSOpenPanel features
  - **multiple** - Enable multiple file selection
  - **create** - Allow NSOpenPanel to create folders
  - **hidden** - Enable hidden directories
- **ADir** - Returnable value of path to selected directory / directories

<hr>

## Examples
```Pascal
//NSOpenPanel // Form contains TButton and TEdit.
procedure TNSDialogsTestForm.NSOpenPanelButton (Sender: TObject);
var
  ADir: String;
begin
  if InvokeNSOpenPanel ('Select Photoshop project', '/Applications/', 'multiple others create', ['psd', 'psb'], ADir) then
    NSOpenPanelPath.Text := ADir
  else
    NSOpenPanelPath.Text := '';
end;
```
