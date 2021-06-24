# Blazor 的演練教室 - 從務門到實務 - Configuration in Blazor

## Client WebAssembly 範例原始程式碼

(1). 設定 appSettings.json

{
  "ConnectionStrings": {
    "DefaultConnection": "Server=(localdb)\\MSSQLLocalDB...(略)"
  },
  "appSettings": {
    "AdminEMail": "gelis.wu@mentortrust.com",
    "UserChtName": "使用者中文名稱",
    "Title": "職稱"
  }
}

(2). 撰寫程式碼

string fileName = "BlazorClientAssembly1.appsettings.json";
var stream = Assembly.GetExecutingAssembly()
	.GetManifestResourceStream(fileName);

var configuration = new ConfigurationBuilder()
	.AddJsonStream(stream)
	.Build();

IConfigurationSection appSettings 
	= configuration.GetSection("appSettings");
            
AdminEMail = appSettings.GetSection("AdminEMail").Value;
UserChtName = appSettings.GetSection("UserChtName").Value;
Title = appSettings.GetSection("Title").Value;

