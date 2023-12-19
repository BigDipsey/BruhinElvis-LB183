## Handlungsziel 3: Authentifizierung und Autorisierung

### Auswahl und Beschreibung des Artefakts
Für dieses Handlungsziel habe ich die Authentifizierung und Autorisierung in der Insecure App gewählt, das eine Zwei-Faktor-Authentifizierung implementiert. Diese Implementierung nutzt die Google Authenticator-App als zweiten Faktor. Es wurden Screenshots des Prozesses erstellt, die zeigen, wie die Authentifizierung funktioniert.

![Bild 1](https://github.com/BigDipsey/BruhinElvis-LB183/assets/89131634/ba42ba74-86e2-4ab6-92a6-f764d407b370)
<img src="https://github.com/BigDipsey/BruhinElvis-LB183/assets/89131634/f3fc883b-b264-44a2-8995-4c465e6a4c1a" style="height: 700;">
<img src="https://github.com/BigDipsey/BruhinElvis-LB183/assets/89131634/7a3f7af9-d988-448d-8c2e-794d94de7983" width="300">

Ein Teil des Codes:
```C#
namespace M183.Controllers
{
    [Route("api/[controller]")]
    [Authorize]
    [ApiController]
    public class AuthController : ControllerBase
    {
        private readonly NewsAppContext _context;
        private readonly IConfiguration _configuration;
        private readonly IUserService _userService;

        public AuthController(NewsAppContext context, IConfiguration configuration, IUserService userService)
        {
            _context = context;
            _configuration = configuration;
            _userService = userService;
        }

        /// <summary>
        /// Enable 2FA for user using password and username
        /// </summary>
        /// <response code="200">Login successfull</response>
        /// <response code="400">Bad request</response>
        /// <response code="401">Login failed</response>
        [HttpPost]
        [ProducesResponseType(200)]
        [ProducesResponseType(404)]
        public ActionResult<Auth2FADto> Enable2FA()
        {
            var user = _context.Users.Find(_userService.GetUserId());
            if (user == null)
            {
                return NotFound(string.Format("User {0} not found", _userService.GetUsername()));
            }
            {
                var secretKey = Guid.NewGuid().ToString().Replace("-", "").Substring(0, 10);
                string userUniqueKey = user.Username + secretKey;
                string issuer = _configuration.GetSection("Jwt:Issuer").Value!;
                TwoFactorAuthenticator authenticator = new TwoFactorAuthenticator();
                SetupCode setupInfo = authenticator.GenerateSetupCode(issuer, user.Username, userUniqueKey, false, 3);

                user.SecretKey2FA = secretKey;
                _context.Update(user);
                _context.SaveChanges();

                Auth2FADto auth2FADto = new Auth2FADto();
                auth2FADto.QrCodeSetupImageUrl = setupInfo.QrCodeSetupImageUrl;

                return Ok(auth2FADto);
            }
        }
    }
}

```


### Nachweis der Zielerreichung
Durch das hinzufügen des Authentifizierung Mechanismus und der Dokumentation des Authentifizierungsprozesses in der Insecure App habe ich gezeigt, wie man eine Zwei-Faktor-Authentifizierung implementieren kann. Die Screenshots dienen als Nachweis.

### Erklärung des Artefakts
Integration von Zwei-Faktor-Authentifizierung in einer Webanwendung. Was zu einer zusätzlichen sicherheit des Benutzerkontos führt.

### Kritische Beurteilung
Ich habe das Handlungsziel abgeschlossen, zuerst verstand ich den Grund wieso man das tuet nicht den schlussendlich ist alles Digital und die 2 Ebene des Schutzes ist nicht wie ein Physikalischer Schlüssel nach etwas rechere fand ich jedoch heraus das es dem Angreifer auch wie bei einem Echten schlüssel schwiriger gemacht wird diesen zu fälschen.
