# Blazor ���t�m�Ы� - �q�Ȫ����� - Configuration in Blazor

## Client WebAssembly �d�ҭ�l�{���X

(1). �]�w appSettings.json

{
  "ConnectionStrings": {
    "DefaultConnection": "Server=(localdb)\\MSSQLLocalDB...(��)"
  },
  "appSettings": {
    "AdminEMail": "gelis.wu@mentortrust.com",
    "UserChtName": "�ϥΪ̤���W��",
    "Title": "¾��"
  }
}

(2). ���g�{���X

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

