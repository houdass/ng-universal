# Angular Universal
  * https://github.com/angular/angular-cli/wiki/stories-universal-rendering
  * npm i -D @angular/platform-server
  * 
  * <pre>
     const params = new HttpParams().append('auth', 'some-token');
     const headers = const headers = new HttpHeaders().append('Authorization', 'Bearer Ad5jar8eq ..');
     return this.httpClient.get<Recipe[]>(this.url , {
      observe: 'body', // response, events, but default: body 
      responseType: 'json', // text, arraybuffer, blob but default: json
      params,
      headers
     })</pre>
  * To make a request with progress events enabled, you can create an instance of HttpRequest with the reportProgress option set true to enable tracking of progress events.
  * <pre>const req = new HttpRequest('PUT', this.url, this.recipeService.getRecipes(), {
       reportProgress: true
     });
     return this.httpClient.request(req);</pre>
  * Interceptors
    * <pre>import { HttpEvent, HttpHandler, HttpInterceptor, HttpRequest } from '@angular/common/http';
      import { Observable } from 'rxjs/Observable';
      import { Injectable } from '@angular/core';
      import { AuthService } from '../auth/auth.service';
         
      @Injectable()
      export class AuthInterceptor implements HttpInterceptor {
         
        constructor(private authService: AuthService) {}
         
        intercept(req: HttpRequest<any>, next: HttpHandler): Observable<HttpEvent<any>> {
          console.log('Intercepted', req);
          const copiedReq = req.clone({ params: req.params.set('auth', this.authService.getToken()) });
          return next.handle(copiedReq);
        }
      }</pre>
      
    * <pre>providers: [
       ...
       { provide: HTTP_INTERCEPTORS, useClass: AuthInterceptor, multi: true },
       { provide: HTTP_INTERCEPTORS, useClass: LoggingInterceptor, multi: true }
      ]</pre>
           
# Store
  * npm i -S @ngrx/store
  * npm i -S @ngrx/effects
  * npm i -S @ngrx/router-store
  * npm i -S @ngrx/store-devtools & https://goo.gl/LLq8A9

