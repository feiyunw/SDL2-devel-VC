# SDL2-devel-VC
Collected and organized SDL2 VC development packages.

# License
SDL 2.0 and newer are available under the zlib license. This license allows you to use SDL freely in any software.
Check the license files in lib/ for SDL2 and its dependencies.

# SDL 2.0 API by Category
## Basics
### SDL.h - Initialization and Shutdown
	extern DECLSPEC int SDLCALL SDL_Init(Uint32 flags);
	extern DECLSPEC int SDLCALL SDL_InitSubSystem(Uint32 flags);
	extern DECLSPEC void SDLCALL SDL_QuitSubSystem(Uint32 flags);
	extern DECLSPEC Uint32 SDLCALL SDL_WasInit(Uint32 flags);
	extern DECLSPEC void SDLCALL SDL_Quit(void);
### SDL_hints.h - Configuration Variables
	extern DECLSPEC SDL_bool SDLCALL SDL_SetHintWithPriority(const char *name,
	                                                         const char *value,
	                                                         SDL_HintPriority priority);
	extern DECLSPEC SDL_bool SDLCALL SDL_SetHint(const char *name,
	                                             const char *value);
	extern DECLSPEC const char * SDLCALL SDL_GetHint(const char *name);
	extern DECLSPEC SDL_bool SDLCALL SDL_GetHintBoolean(const char *name, SDL_bool default_value);
	extern DECLSPEC void SDLCALL SDL_AddHintCallback(const char *name,
	                                                 SDL_HintCallback callback,
	                                                 void *userdata);
	extern DECLSPEC void SDLCALL SDL_DelHintCallback(const char *name,
	                                                 SDL_HintCallback callback,
	                                                 void *userdata);
	extern DECLSPEC void SDLCALL SDL_ClearHints(void);
### SDL_error.h - Error Handling
	extern DECLSPEC int SDLCALL SDL_SetError(SDL_PRINTF_FORMAT_STRING const char *fmt, ...) SDL_PRINTF_VARARG_FUNC(1);
	extern DECLSPEC const char *SDLCALL SDL_GetError(void);
	extern DECLSPEC void SDLCALL SDL_ClearError(void);
	extern DECLSPEC int SDLCALL SDL_Error(SDL_errorcode code);
### SDL_log.h - Log Handling
	extern DECLSPEC void SDLCALL SDL_LogSetAllPriority(SDL_LogPriority priority);
	extern DECLSPEC void SDLCALL SDL_LogSetPriority(int category,
	                                                SDL_LogPriority priority);
	extern DECLSPEC SDL_LogPriority SDLCALL SDL_LogGetPriority(int category);
	extern DECLSPEC void SDLCALL SDL_LogResetPriorities(void);
	extern DECLSPEC void SDLCALL SDL_Log(SDL_PRINTF_FORMAT_STRING const char *fmt, ...) SDL_PRINTF_VARARG_FUNC(1);
	extern DECLSPEC void SDLCALL SDL_LogVerbose(int category, SDL_PRINTF_FORMAT_STRING const char *fmt, ...) SDL_PRINTF_VARARG_FUNC(2);
	extern DECLSPEC void SDLCALL SDL_LogDebug(int category, SDL_PRINTF_FORMAT_STRING const char *fmt, ...) SDL_PRINTF_VARARG_FUNC(2);
	extern DECLSPEC void SDLCALL SDL_LogInfo(int category, SDL_PRINTF_FORMAT_STRING const char *fmt, ...) SDL_PRINTF_VARARG_FUNC(2);
	extern DECLSPEC void SDLCALL SDL_LogWarn(int category, SDL_PRINTF_FORMAT_STRING const char *fmt, ...) SDL_PRINTF_VARARG_FUNC(2);
	extern DECLSPEC void SDLCALL SDL_LogError(int category, SDL_PRINTF_FORMAT_STRING const char *fmt, ...) SDL_PRINTF_VARARG_FUNC(2);
	extern DECLSPEC void SDLCALL SDL_LogCritical(int category, SDL_PRINTF_FORMAT_STRING const char *fmt, ...) SDL_PRINTF_VARARG_FUNC(2);
	extern DECLSPEC void SDLCALL SDL_LogMessage(int category,
	                                            SDL_LogPriority priority,
	                                            SDL_PRINTF_FORMAT_STRING const char *fmt, ...) SDL_PRINTF_VARARG_FUNC(3);
	extern DECLSPEC void SDLCALL SDL_LogMessageV(int category,
	                                             SDL_LogPriority priority,
	                                             const char *fmt, va_list ap);
	extern DECLSPEC void SDLCALL SDL_LogGetOutputFunction(SDL_LogOutputFunction *callback, void **userdata);
	extern DECLSPEC void SDLCALL SDL_LogSetOutputFunction(SDL_LogOutputFunction callback, void *userdata);
### SDL_assert.h - Assertions
	#elif SDL_ASSERT_LEVEL == 1  /* release settings. */
	#   define SDL_assert(condition) SDL_disabled_assert(condition)
	#   define SDL_assert_release(condition) SDL_enabled_assert(condition)
	#elif SDL_ASSERT_LEVEL == 2  /* normal settings. */
	#   define SDL_assert(condition) SDL_enabled_assert(condition)
	#   define SDL_assert_release(condition) SDL_enabled_assert(condition)
	#define SDL_assert_always(condition) SDL_enabled_assert(condition)
	extern DECLSPEC void SDLCALL SDL_SetAssertionHandler(
	                                            SDL_AssertionHandler handler,
	                                            void *userdata);
	extern DECLSPEC SDL_AssertionHandler SDLCALL SDL_GetDefaultAssertionHandler(void);
	extern DECLSPEC SDL_AssertionHandler SDLCALL SDL_GetAssertionHandler(void **puserdata);
	extern DECLSPEC const SDL_AssertData * SDLCALL SDL_GetAssertionReport(void);
	extern DECLSPEC void SDLCALL SDL_ResetAssertionReport(void);
### SDL_version.h - Querying SDL Version
	extern DECLSPEC void SDLCALL SDL_GetVersion(SDL_version * ver);
	extern DECLSPEC const char *SDLCALL SDL_GetRevision(void);
	extern DECLSPEC int SDLCALL SDL_GetRevisionNumber(void);
## Video
### SDL_video.h - Display and Window Management
	extern DECLSPEC int SDLCALL SDL_GetNumVideoDrivers(void);
	extern DECLSPEC const char *SDLCALL SDL_GetVideoDriver(int index);
	extern DECLSPEC int SDLCALL SDL_VideoInit(const char *driver_name);
	extern DECLSPEC void SDLCALL SDL_VideoQuit(void);
	extern DECLSPEC const char *SDLCALL SDL_GetCurrentVideoDriver(void);
	extern DECLSPEC int SDLCALL SDL_GetNumVideoDisplays(void);
	extern DECLSPEC const char * SDLCALL SDL_GetDisplayName(int displayIndex);
	extern DECLSPEC int SDLCALL SDL_GetDisplayBounds(int displayIndex, SDL_Rect * rect);
	extern DECLSPEC int SDLCALL SDL_GetDisplayDPI(int displayIndex, float * ddpi, float * hdpi, float * vdpi);
	extern DECLSPEC int SDLCALL SDL_GetDisplayUsableBounds(int displayIndex, SDL_Rect * rect);
	extern DECLSPEC int SDLCALL SDL_GetNumDisplayModes(int displayIndex);
	extern DECLSPEC int SDLCALL SDL_GetDisplayMode(int displayIndex, int modeIndex,
	                                               SDL_DisplayMode * mode);
	extern DECLSPEC int SDLCALL SDL_GetDesktopDisplayMode(int displayIndex, SDL_DisplayMode * mode);
	extern DECLSPEC int SDLCALL SDL_GetCurrentDisplayMode(int displayIndex, SDL_DisplayMode * mode);
	extern DECLSPEC SDL_DisplayMode * SDLCALL SDL_GetClosestDisplayMode(int displayIndex, const SDL_DisplayMode * mode, SDL_DisplayMode * closest);
	extern DECLSPEC int SDLCALL SDL_GetWindowDisplayIndex(SDL_Window * window);
	extern DECLSPEC int SDLCALL SDL_SetWindowDisplayMode(SDL_Window * window,
	                                                     const SDL_DisplayMode
	                                                         * mode);
	extern DECLSPEC int SDLCALL SDL_GetWindowDisplayMode(SDL_Window * window,
	                                                     SDL_DisplayMode * mode);
	extern DECLSPEC Uint32 SDLCALL SDL_GetWindowPixelFormat(SDL_Window * window);
	extern DECLSPEC SDL_Window * SDLCALL SDL_CreateWindow(const char *title,
	                                                      int x, int y, int w,
	                                                      int h, Uint32 flags);
	extern DECLSPEC SDL_Window * SDLCALL SDL_CreateWindowFrom(const void *data);
	extern DECLSPEC Uint32 SDLCALL SDL_GetWindowID(SDL_Window * window);
	extern DECLSPEC SDL_Window * SDLCALL SDL_GetWindowFromID(Uint32 id);
	extern DECLSPEC Uint32 SDLCALL SDL_GetWindowFlags(SDL_Window * window);
	extern DECLSPEC void SDLCALL SDL_SetWindowTitle(SDL_Window * window,
	                                                const char *title);
	extern DECLSPEC const char *SDLCALL SDL_GetWindowTitle(SDL_Window * window);
	extern DECLSPEC void SDLCALL SDL_SetWindowIcon(SDL_Window * window,
	                                               SDL_Surface * icon);
	extern DECLSPEC void* SDLCALL SDL_SetWindowData(SDL_Window * window,
	                                                const char *name,
	                                                void *userdata);
	extern DECLSPEC void *SDLCALL SDL_GetWindowData(SDL_Window * window,
	                                                const char *name);
	extern DECLSPEC void SDLCALL SDL_SetWindowPosition(SDL_Window * window,
	                                                   int x, int y);
	extern DECLSPEC void SDLCALL SDL_GetWindowPosition(SDL_Window * window,
	                                                   int *x, int *y);
	extern DECLSPEC void SDLCALL SDL_SetWindowSize(SDL_Window * window, int w,
	                                               int h);
	extern DECLSPEC void SDLCALL SDL_GetWindowSize(SDL_Window * window, int *w,
	                                               int *h);
	extern DECLSPEC int SDLCALL SDL_GetWindowBordersSize(SDL_Window * window,
	                                                     int *top, int *left,
	                                                     int *bottom, int *right);
	extern DECLSPEC void SDLCALL SDL_SetWindowMinimumSize(SDL_Window * window,
	                                                      int min_w, int min_h);
	extern DECLSPEC void SDLCALL SDL_GetWindowMinimumSize(SDL_Window * window,
	                                                      int *w, int *h);
	extern DECLSPEC void SDLCALL SDL_SetWindowMaximumSize(SDL_Window * window,
	                                                      int max_w, int max_h);
	extern DECLSPEC void SDLCALL SDL_GetWindowMaximumSize(SDL_Window * window,
	                                                      int *w, int *h);
	extern DECLSPEC void SDLCALL SDL_SetWindowBordered(SDL_Window * window,
	                                                   SDL_bool bordered);
	extern DECLSPEC void SDLCALL SDL_SetWindowResizable(SDL_Window * window,
	                                                    SDL_bool resizable);
	extern DECLSPEC void SDLCALL SDL_ShowWindow(SDL_Window * window);
	extern DECLSPEC void SDLCALL SDL_HideWindow(SDL_Window * window);
	extern DECLSPEC void SDLCALL SDL_RaiseWindow(SDL_Window * window);
	extern DECLSPEC void SDLCALL SDL_MaximizeWindow(SDL_Window * window);
	extern DECLSPEC void SDLCALL SDL_MinimizeWindow(SDL_Window * window);
	extern DECLSPEC void SDLCALL SDL_RestoreWindow(SDL_Window * window);
	extern DECLSPEC int SDLCALL SDL_SetWindowFullscreen(SDL_Window * window,
	                                                    Uint32 flags);
	extern DECLSPEC SDL_Surface * SDLCALL SDL_GetWindowSurface(SDL_Window * window);
	extern DECLSPEC int SDLCALL SDL_UpdateWindowSurface(SDL_Window * window);
	extern DECLSPEC int SDLCALL SDL_UpdateWindowSurfaceRects(SDL_Window * window,
	                                                         const SDL_Rect * rects,
	                                                         int numrects);
	extern DECLSPEC void SDLCALL SDL_SetWindowGrab(SDL_Window * window,
	                                               SDL_bool grabbed);
	extern DECLSPEC SDL_bool SDLCALL SDL_GetWindowGrab(SDL_Window * window);
	extern DECLSPEC SDL_Window * SDLCALL SDL_GetGrabbedWindow(void);
	extern DECLSPEC int SDLCALL SDL_SetWindowBrightness(SDL_Window * window, float brightness);
	extern DECLSPEC float SDLCALL SDL_GetWindowBrightness(SDL_Window * window);
	extern DECLSPEC int SDLCALL SDL_SetWindowOpacity(SDL_Window * window, float opacity);
	extern DECLSPEC int SDLCALL SDL_GetWindowOpacity(SDL_Window * window, float * out_opacity);
	extern DECLSPEC int SDLCALL SDL_SetWindowModalFor(SDL_Window * modal_window, SDL_Window * parent_window);
	extern DECLSPEC int SDLCALL SDL_SetWindowInputFocus(SDL_Window * window);
	extern DECLSPEC int SDLCALL SDL_SetWindowGammaRamp(SDL_Window * window,
	                                                   const Uint16 * red,
	                                                   const Uint16 * green,
	                                                   const Uint16 * blue);
	extern DECLSPEC int SDLCALL SDL_GetWindowGammaRamp(SDL_Window * window,
	                                                   Uint16 * red,
	                                                   Uint16 * green,
	                                                   Uint16 * blue);
	extern DECLSPEC int SDLCALL SDL_SetWindowHitTest(SDL_Window * window,
	                                                 SDL_HitTest callback,
	                                                 void *callback_data);
	extern DECLSPEC void SDLCALL SDL_DestroyWindow(SDL_Window * window);
	extern DECLSPEC SDL_bool SDLCALL SDL_IsScreenSaverEnabled(void);
	extern DECLSPEC void SDLCALL SDL_EnableScreenSaver(void);
	extern DECLSPEC void SDLCALL SDL_DisableScreenSaver(void);
	extern DECLSPEC int SDLCALL SDL_GL_LoadLibrary(const char *path);
	extern DECLSPEC void *SDLCALL SDL_GL_GetProcAddress(const char *proc);
	extern DECLSPEC void SDLCALL SDL_GL_UnloadLibrary(void);
	extern DECLSPEC SDL_bool SDLCALL SDL_GL_ExtensionSupported(const char
	                                                           *extension);
	extern DECLSPEC void SDLCALL SDL_GL_ResetAttributes(void);
	extern DECLSPEC int SDLCALL SDL_GL_SetAttribute(SDL_GLattr attr, int value);
	extern DECLSPEC int SDLCALL SDL_GL_GetAttribute(SDL_GLattr attr, int *value);
	extern DECLSPEC SDL_GLContext SDLCALL SDL_GL_CreateContext(SDL_Window *
	                                                           window);
	extern DECLSPEC int SDLCALL SDL_GL_MakeCurrent(SDL_Window * window,
	                                               SDL_GLContext context);
	extern DECLSPEC SDL_Window* SDLCALL SDL_GL_GetCurrentWindow(void);
	extern DECLSPEC SDL_GLContext SDLCALL SDL_GL_GetCurrentContext(void);
	extern DECLSPEC void SDLCALL SDL_GL_GetDrawableSize(SDL_Window * window, int *w,
	                                                    int *h);
	extern DECLSPEC int SDLCALL SDL_GL_SetSwapInterval(int interval);
	extern DECLSPEC int SDLCALL SDL_GL_GetSwapInterval(void);
	extern DECLSPEC void SDLCALL SDL_GL_SwapWindow(SDL_Window * window);
	extern DECLSPEC void SDLCALL SDL_GL_DeleteContext(SDL_GLContext context);
### SDL_render.h - 2D Accelerated Rendering
	extern DECLSPEC int SDLCALL SDL_GetNumRenderDrivers(void);
	extern DECLSPEC int SDLCALL SDL_GetRenderDriverInfo(int index,
	                                                    SDL_RendererInfo * info);
	extern DECLSPEC int SDLCALL SDL_CreateWindowAndRenderer(
	                                int width, int height, Uint32 window_flags,
	                                SDL_Window **window, SDL_Renderer **renderer);
	extern DECLSPEC SDL_Renderer * SDLCALL SDL_CreateRenderer(SDL_Window * window,
	                                               int index, Uint32 flags);
	extern DECLSPEC SDL_Renderer * SDLCALL SDL_CreateSoftwareRenderer(SDL_Surface * surface);
	extern DECLSPEC SDL_Renderer * SDLCALL SDL_GetRenderer(SDL_Window * window);
	extern DECLSPEC int SDLCALL SDL_GetRendererInfo(SDL_Renderer * renderer,
	                                                SDL_RendererInfo * info);
	extern DECLSPEC int SDLCALL SDL_GetRendererOutputSize(SDL_Renderer * renderer,
	                                                      int *w, int *h);
	extern DECLSPEC SDL_Texture * SDLCALL SDL_CreateTexture(SDL_Renderer * renderer,
	                                                        Uint32 format,
	                                                        int access, int w,
	                                                        int h);
	extern DECLSPEC SDL_Texture * SDLCALL SDL_CreateTextureFromSurface(SDL_Renderer * renderer, SDL_Surface * surface);
	extern DECLSPEC int SDLCALL SDL_QueryTexture(SDL_Texture * texture,
	                                             Uint32 * format, int *access,
	                                             int *w, int *h);
	extern DECLSPEC int SDLCALL SDL_SetTextureColorMod(SDL_Texture * texture,
	                                                   Uint8 r, Uint8 g, Uint8 b);
	extern DECLSPEC int SDLCALL SDL_GetTextureColorMod(SDL_Texture * texture,
	                                                   Uint8 * r, Uint8 * g,
	                                                   Uint8 * b);
	extern DECLSPEC int SDLCALL SDL_SetTextureAlphaMod(SDL_Texture * texture,
	                                                   Uint8 alpha);
	extern DECLSPEC int SDLCALL SDL_GetTextureAlphaMod(SDL_Texture * texture,
	                                                   Uint8 * alpha);
	extern DECLSPEC int SDLCALL SDL_SetTextureBlendMode(SDL_Texture * texture,
	                                                    SDL_BlendMode blendMode);
	extern DECLSPEC int SDLCALL SDL_GetTextureBlendMode(SDL_Texture * texture,
	                                                    SDL_BlendMode *blendMode);
	extern DECLSPEC int SDLCALL SDL_UpdateTexture(SDL_Texture * texture,
	                                              const SDL_Rect * rect,
	                                              const void *pixels, int pitch);
	extern DECLSPEC int SDLCALL SDL_UpdateYUVTexture(SDL_Texture * texture,
	                                                 const SDL_Rect * rect,
	                                                 const Uint8 *Yplane, int Ypitch,
	                                                 const Uint8 *Uplane, int Upitch,
	                                                 const Uint8 *Vplane, int Vpitch);
	extern DECLSPEC int SDLCALL SDL_LockTexture(SDL_Texture * texture,
	                                            const SDL_Rect * rect,
	                                            void **pixels, int *pitch);
	extern DECLSPEC void SDLCALL SDL_UnlockTexture(SDL_Texture * texture);
	extern DECLSPEC SDL_bool SDLCALL SDL_RenderTargetSupported(SDL_Renderer *renderer);
	extern DECLSPEC int SDLCALL SDL_SetRenderTarget(SDL_Renderer *renderer,
	                                                SDL_Texture *texture);
	extern DECLSPEC SDL_Texture * SDLCALL SDL_GetRenderTarget(SDL_Renderer *renderer);
	extern DECLSPEC int SDLCALL SDL_RenderSetLogicalSize(SDL_Renderer * renderer, int w, int h);
	extern DECLSPEC void SDLCALL SDL_RenderGetLogicalSize(SDL_Renderer * renderer, int *w, int *h);
	extern DECLSPEC int SDLCALL SDL_RenderSetIntegerScale(SDL_Renderer * renderer,
	                                                      SDL_bool enable);
	extern DECLSPEC SDL_bool SDLCALL SDL_RenderGetIntegerScale(SDL_Renderer * renderer);
	extern DECLSPEC int SDLCALL SDL_RenderSetViewport(SDL_Renderer * renderer,
	                                                  const SDL_Rect * rect);
	extern DECLSPEC void SDLCALL SDL_RenderGetViewport(SDL_Renderer * renderer,
	                                                   SDL_Rect * rect);
	extern DECLSPEC int SDLCALL SDL_RenderSetClipRect(SDL_Renderer * renderer,
	                                                  const SDL_Rect * rect);
	extern DECLSPEC void SDLCALL SDL_RenderGetClipRect(SDL_Renderer * renderer,
	                                                   SDL_Rect * rect);
	extern DECLSPEC SDL_bool SDLCALL SDL_RenderIsClipEnabled(SDL_Renderer * renderer);
	extern DECLSPEC int SDLCALL SDL_RenderSetScale(SDL_Renderer * renderer,
	                                               float scaleX, float scaleY);
	extern DECLSPEC void SDLCALL SDL_RenderGetScale(SDL_Renderer * renderer,
	                                               float *scaleX, float *scaleY);
	extern DECLSPEC int SDLCALL SDL_SetRenderDrawColor(SDL_Renderer * renderer,
	                                           Uint8 r, Uint8 g, Uint8 b,
	                                           Uint8 a);
	extern DECLSPEC int SDLCALL SDL_GetRenderDrawColor(SDL_Renderer * renderer,
	                                           Uint8 * r, Uint8 * g, Uint8 * b,
	                                           Uint8 * a);
	extern DECLSPEC int SDLCALL SDL_SetRenderDrawBlendMode(SDL_Renderer * renderer,
	                                                       SDL_BlendMode blendMode);
	extern DECLSPEC int SDLCALL SDL_GetRenderDrawBlendMode(SDL_Renderer * renderer,
	                                                       SDL_BlendMode *blendMode);
	extern DECLSPEC int SDLCALL SDL_RenderClear(SDL_Renderer * renderer);
	extern DECLSPEC int SDLCALL SDL_RenderDrawPoint(SDL_Renderer * renderer,
	                                                int x, int y);
	extern DECLSPEC int SDLCALL SDL_RenderDrawPoints(SDL_Renderer * renderer,
	                                                 const SDL_Point * points,
	                                                 int count);
	extern DECLSPEC int SDLCALL SDL_RenderDrawLine(SDL_Renderer * renderer,
	                                               int x1, int y1, int x2, int y2);
	extern DECLSPEC int SDLCALL SDL_RenderDrawLines(SDL_Renderer * renderer,
	                                                const SDL_Point * points,
	                                                int count);
	extern DECLSPEC int SDLCALL SDL_RenderDrawRect(SDL_Renderer * renderer,
	                                               const SDL_Rect * rect);
	extern DECLSPEC int SDLCALL SDL_RenderDrawRects(SDL_Renderer * renderer,
	                                                const SDL_Rect * rects,
	                                                int count);
	extern DECLSPEC int SDLCALL SDL_RenderFillRect(SDL_Renderer * renderer,
	                                               const SDL_Rect * rect);
	extern DECLSPEC int SDLCALL SDL_RenderFillRects(SDL_Renderer * renderer,
	                                                const SDL_Rect * rects,
	                                                int count);
	extern DECLSPEC int SDLCALL SDL_RenderCopy(SDL_Renderer * renderer,
	                                           SDL_Texture * texture,
	                                           const SDL_Rect * srcrect,
	                                           const SDL_Rect * dstrect);
	extern DECLSPEC int SDLCALL SDL_RenderCopyEx(SDL_Renderer * renderer,
	                                           SDL_Texture * texture,
	                                           const SDL_Rect * srcrect,
	                                           const SDL_Rect * dstrect,
	                                           const double angle,
	                                           const SDL_Point *center,
	                                           const SDL_RendererFlip flip);
	extern DECLSPEC int SDLCALL SDL_RenderReadPixels(SDL_Renderer * renderer,
	                                                 const SDL_Rect * rect,
	                                                 Uint32 format,
	                                                 void *pixels, int pitch);
	extern DECLSPEC void SDLCALL SDL_RenderPresent(SDL_Renderer * renderer);
	extern DECLSPEC void SDLCALL SDL_DestroyTexture(SDL_Texture * texture);
	extern DECLSPEC void SDLCALL SDL_DestroyRenderer(SDL_Renderer * renderer);
	extern DECLSPEC int SDLCALL SDL_GL_BindTexture(SDL_Texture *texture, float *texw, float *texh);
	extern DECLSPEC int SDLCALL SDL_GL_UnbindTexture(SDL_Texture *texture);
### SDL_pixels.h - Pixel Formats and Conversion Routines
	extern DECLSPEC const char* SDLCALL SDL_GetPixelFormatName(Uint32 format);
	extern DECLSPEC SDL_bool SDLCALL SDL_PixelFormatEnumToMasks(Uint32 format,
	                                                            int *bpp,
	                                                            Uint32 * Rmask,
	                                                            Uint32 * Gmask,
	                                                            Uint32 * Bmask,
	                                                            Uint32 * Amask);
	extern DECLSPEC Uint32 SDLCALL SDL_MasksToPixelFormatEnum(int bpp,
	                                                          Uint32 Rmask,
	                                                          Uint32 Gmask,
	                                                          Uint32 Bmask,
	                                                          Uint32 Amask);
	extern DECLSPEC SDL_PixelFormat * SDLCALL SDL_AllocFormat(Uint32 pixel_format);
	extern DECLSPEC void SDLCALL SDL_FreeFormat(SDL_PixelFormat *format);
	extern DECLSPEC SDL_Palette *SDLCALL SDL_AllocPalette(int ncolors);
	extern DECLSPEC int SDLCALL SDL_SetPixelFormatPalette(SDL_PixelFormat * format,
	                                                      SDL_Palette *palette);
	extern DECLSPEC int SDLCALL SDL_SetPaletteColors(SDL_Palette * palette,
	                                                 const SDL_Color * colors,
	                                                 int firstcolor, int ncolors);
	extern DECLSPEC void SDLCALL SDL_FreePalette(SDL_Palette * palette);
	extern DECLSPEC Uint32 SDLCALL SDL_MapRGB(const SDL_PixelFormat * format,
	                                          Uint8 r, Uint8 g, Uint8 b);
	extern DECLSPEC Uint32 SDLCALL SDL_MapRGBA(const SDL_PixelFormat * format,
	                                           Uint8 r, Uint8 g, Uint8 b,
	                                           Uint8 a);
	extern DECLSPEC void SDLCALL SDL_GetRGB(Uint32 pixel,
	                                        const SDL_PixelFormat * format,
	                                        Uint8 * r, Uint8 * g, Uint8 * b);
	extern DECLSPEC void SDLCALL SDL_GetRGBA(Uint32 pixel,
	                                         const SDL_PixelFormat * format,
	                                         Uint8 * r, Uint8 * g, Uint8 * b,
	                                         Uint8 * a);
	extern DECLSPEC void SDLCALL SDL_CalculateGammaRamp(float gamma, Uint16 * ramp);
### SDL_rect.h - Rectangle Functions
	extern DECLSPEC SDL_bool SDLCALL SDL_HasIntersection(const SDL_Rect * A,
	                                                     const SDL_Rect * B);
	extern DECLSPEC SDL_bool SDLCALL SDL_IntersectRect(const SDL_Rect * A,
	                                                   const SDL_Rect * B,
	                                                   SDL_Rect * result);
	extern DECLSPEC void SDLCALL SDL_UnionRect(const SDL_Rect * A,
	                                           const SDL_Rect * B,
	                                           SDL_Rect * result);
	extern DECLSPEC SDL_bool SDLCALL SDL_EnclosePoints(const SDL_Point * points,
	                                                   int count,
	                                                   const SDL_Rect * clip,
	                                                   SDL_Rect * result);
	extern DECLSPEC SDL_bool SDLCALL SDL_IntersectRectAndLine(const SDL_Rect *
	                                                          rect, int *X1,
	                                                          int *Y1, int *X2,
	                                                          int *Y2);
### SDL_surface.h - Surface Creation and Simple Drawing
	extern DECLSPEC SDL_Surface *SDLCALL SDL_CreateRGBSurface
	    (Uint32 flags, int width, int height, int depth,
	     Uint32 Rmask, Uint32 Gmask, Uint32 Bmask, Uint32 Amask);
	extern DECLSPEC SDL_Surface *SDLCALL SDL_CreateRGBSurfaceWithFormat
	    (Uint32 flags, int width, int height, int depth, Uint32 format);
	extern DECLSPEC SDL_Surface *SDLCALL SDL_CreateRGBSurfaceFrom(void *pixels,
	                                                              int width,
	                                                              int height,
	                                                              int depth,
	                                                              int pitch,
	                                                              Uint32 Rmask,
	                                                              Uint32 Gmask,
	                                                              Uint32 Bmask,
	                                                              Uint32 Amask);
	extern DECLSPEC SDL_Surface *SDLCALL SDL_CreateRGBSurfaceWithFormatFrom
	    (void *pixels, int width, int height, int depth, int pitch, Uint32 format);
	extern DECLSPEC void SDLCALL SDL_FreeSurface(SDL_Surface * surface);
	extern DECLSPEC int SDLCALL SDL_SetSurfacePalette(SDL_Surface * surface,
	                                                  SDL_Palette * palette);
	extern DECLSPEC int SDLCALL SDL_LockSurface(SDL_Surface * surface);
	extern DECLSPEC void SDLCALL SDL_UnlockSurface(SDL_Surface * surface);
	extern DECLSPEC SDL_Surface *SDLCALL SDL_LoadBMP_RW(SDL_RWops * src,
	                                                    int freesrc);
	extern DECLSPEC int SDLCALL SDL_SaveBMP_RW
	    (SDL_Surface * surface, SDL_RWops * dst, int freedst);
	extern DECLSPEC int SDLCALL SDL_SetSurfaceRLE(SDL_Surface * surface,
	                                              int flag);
	extern DECLSPEC int SDLCALL SDL_SetColorKey(SDL_Surface * surface,
	                                            int flag, Uint32 key);
	extern DECLSPEC int SDLCALL SDL_GetColorKey(SDL_Surface * surface,
	                                            Uint32 * key);
	extern DECLSPEC int SDLCALL SDL_SetSurfaceColorMod(SDL_Surface * surface,
	                                                   Uint8 r, Uint8 g, Uint8 b);
	extern DECLSPEC int SDLCALL SDL_GetSurfaceColorMod(SDL_Surface * surface,
	                                                   Uint8 * r, Uint8 * g,
	                                                   Uint8 * b);
	extern DECLSPEC int SDLCALL SDL_SetSurfaceAlphaMod(SDL_Surface * surface,
	                                                   Uint8 alpha);
	extern DECLSPEC int SDLCALL SDL_GetSurfaceAlphaMod(SDL_Surface * surface,
	                                                   Uint8 * alpha);
	extern DECLSPEC int SDLCALL SDL_SetSurfaceBlendMode(SDL_Surface * surface,
	                                                    SDL_BlendMode blendMode);
	extern DECLSPEC int SDLCALL SDL_GetSurfaceBlendMode(SDL_Surface * surface,
	                                                    SDL_BlendMode *blendMode);
	extern DECLSPEC SDL_bool SDLCALL SDL_SetClipRect(SDL_Surface * surface,
	                                                 const SDL_Rect * rect);
	extern DECLSPEC void SDLCALL SDL_GetClipRect(SDL_Surface * surface,
	                                             SDL_Rect * rect);
	extern DECLSPEC SDL_Surface *SDLCALL SDL_DuplicateSurface(SDL_Surface * surface);
	extern DECLSPEC SDL_Surface *SDLCALL SDL_ConvertSurface
	    (SDL_Surface * src, const SDL_PixelFormat * fmt, Uint32 flags);
	extern DECLSPEC SDL_Surface *SDLCALL SDL_ConvertSurfaceFormat
	    (SDL_Surface * src, Uint32 pixel_format, Uint32 flags);
	extern DECLSPEC int SDLCALL SDL_ConvertPixels(int width, int height,
	                                              Uint32 src_format,
	                                              const void * src, int src_pitch,
	                                              Uint32 dst_format,
	                                              void * dst, int dst_pitch);
	extern DECLSPEC int SDLCALL SDL_FillRect
	    (SDL_Surface * dst, const SDL_Rect * rect, Uint32 color);
	extern DECLSPEC int SDLCALL SDL_FillRects
	    (SDL_Surface * dst, const SDL_Rect * rects, int count, Uint32 color);
	extern DECLSPEC int SDLCALL SDL_UpperBlit
	    (SDL_Surface * src, const SDL_Rect * srcrect,
	     SDL_Surface * dst, SDL_Rect * dstrect);
	extern DECLSPEC int SDLCALL SDL_LowerBlit
	    (SDL_Surface * src, SDL_Rect * srcrect,
	     SDL_Surface * dst, SDL_Rect * dstrect);
	extern DECLSPEC int SDLCALL SDL_SoftStretch(SDL_Surface * src,
	                                            const SDL_Rect * srcrect,
	                                            SDL_Surface * dst,
	                                            const SDL_Rect * dstrect);
	extern DECLSPEC int SDLCALL SDL_UpperBlitScaled
	    (SDL_Surface * src, const SDL_Rect * srcrect,
	    SDL_Surface * dst, SDL_Rect * dstrect);
	extern DECLSPEC int SDLCALL SDL_LowerBlitScaled
	    (SDL_Surface * src, SDL_Rect * srcrect,
	    SDL_Surface * dst, SDL_Rect * dstrect);
### SDL_syswm.h - Platform-specific Window Management
	extern DECLSPEC SDL_bool SDLCALL SDL_GetWindowWMInfo(SDL_Window * window,
	                                                     SDL_SysWMinfo * info);
### SDL_clipboard.h - Clipboard Handling
	extern DECLSPEC int SDLCALL SDL_SetClipboardText(const char *text);
	extern DECLSPEC char * SDLCALL SDL_GetClipboardText(void);
	extern DECLSPEC SDL_bool SDLCALL SDL_HasClipboardText(void);
## Input Events
### SDL_events.h - Event Handling
	extern DECLSPEC void SDLCALL SDL_PumpEvents(void);
	extern DECLSPEC int SDLCALL SDL_PeepEvents(SDL_Event * events, int numevents,
	                                           SDL_eventaction action,
	                                           Uint32 minType, Uint32 maxType);
	extern DECLSPEC SDL_bool SDLCALL SDL_HasEvent(Uint32 type);
	extern DECLSPEC SDL_bool SDLCALL SDL_HasEvents(Uint32 minType, Uint32 maxType);
	extern DECLSPEC void SDLCALL SDL_FlushEvent(Uint32 type);
	extern DECLSPEC void SDLCALL SDL_FlushEvents(Uint32 minType, Uint32 maxType);
	extern DECLSPEC int SDLCALL SDL_PollEvent(SDL_Event * event);
	extern DECLSPEC int SDLCALL SDL_WaitEvent(SDL_Event * event);
	extern DECLSPEC int SDLCALL SDL_WaitEventTimeout(SDL_Event * event,
	                                                 int timeout);
	extern DECLSPEC int SDLCALL SDL_PushEvent(SDL_Event * event);
	extern DECLSPEC void SDLCALL SDL_SetEventFilter(SDL_EventFilter filter,
	                                                void *userdata);
	extern DECLSPEC SDL_bool SDLCALL SDL_GetEventFilter(SDL_EventFilter * filter,
	                                                    void **userdata);
	extern DECLSPEC void SDLCALL SDL_AddEventWatch(SDL_EventFilter filter,
	                                               void *userdata);
	extern DECLSPEC void SDLCALL SDL_DelEventWatch(SDL_EventFilter filter,
	                                               void *userdata);
	extern DECLSPEC void SDLCALL SDL_FilterEvents(SDL_EventFilter filter,
	                                              void *userdata);
	extern DECLSPEC Uint8 SDLCALL SDL_EventState(Uint32 type, int state);
	extern DECLSPEC Uint32 SDLCALL SDL_RegisterEvents(int numevents);
### SDL_keyboard.h - Keyboard Support
	extern DECLSPEC SDL_Window * SDLCALL SDL_GetKeyboardFocus(void);
	extern DECLSPEC const Uint8 *SDLCALL SDL_GetKeyboardState(int *numkeys);
	extern DECLSPEC SDL_Keymod SDLCALL SDL_GetModState(void);
	extern DECLSPEC void SDLCALL SDL_SetModState(SDL_Keymod modstate);
	extern DECLSPEC SDL_Keycode SDLCALL SDL_GetKeyFromScancode(SDL_Scancode scancode);
	extern DECLSPEC SDL_Scancode SDLCALL SDL_GetScancodeFromKey(SDL_Keycode key);
	extern DECLSPEC const char *SDLCALL SDL_GetScancodeName(SDL_Scancode scancode);
	extern DECLSPEC SDL_Scancode SDLCALL SDL_GetScancodeFromName(const char *name);
	extern DECLSPEC const char *SDLCALL SDL_GetKeyName(SDL_Keycode key);
	extern DECLSPEC SDL_Keycode SDLCALL SDL_GetKeyFromName(const char *name);
	extern DECLSPEC void SDLCALL SDL_StartTextInput(void);
	extern DECLSPEC SDL_bool SDLCALL SDL_IsTextInputActive(void);
	extern DECLSPEC void SDLCALL SDL_StopTextInput(void);
	extern DECLSPEC void SDLCALL SDL_SetTextInputRect(SDL_Rect *rect);
	extern DECLSPEC SDL_bool SDLCALL SDL_HasScreenKeyboardSupport(void);
	extern DECLSPEC SDL_bool SDLCALL SDL_IsScreenKeyboardShown(SDL_Window *window);
### SDL_mouse.h - Mouse Support
	extern DECLSPEC SDL_Window * SDLCALL SDL_GetMouseFocus(void);
	extern DECLSPEC Uint32 SDLCALL SDL_GetMouseState(int *x, int *y);
	extern DECLSPEC Uint32 SDLCALL SDL_GetGlobalMouseState(int *x, int *y);
	extern DECLSPEC Uint32 SDLCALL SDL_GetRelativeMouseState(int *x, int *y);
	extern DECLSPEC void SDLCALL SDL_WarpMouseInWindow(SDL_Window * window,
	                                                   int x, int y);
	extern DECLSPEC int SDLCALL SDL_WarpMouseGlobal(int x, int y);
	extern DECLSPEC int SDLCALL SDL_SetRelativeMouseMode(SDL_bool enabled);
	extern DECLSPEC int SDLCALL SDL_CaptureMouse(SDL_bool enabled);
	extern DECLSPEC SDL_bool SDLCALL SDL_GetRelativeMouseMode(void);
	extern DECLSPEC SDL_Cursor *SDLCALL SDL_CreateCursor(const Uint8 * data,
	                                                     const Uint8 * mask,
	                                                     int w, int h, int hot_x,
	                                                     int hot_y);
	extern DECLSPEC SDL_Cursor *SDLCALL SDL_CreateColorCursor(SDL_Surface *surface,
	                                                          int hot_x,
	                                                          int hot_y);
	extern DECLSPEC SDL_Cursor *SDLCALL SDL_CreateSystemCursor(SDL_SystemCursor id);
	extern DECLSPEC void SDLCALL SDL_SetCursor(SDL_Cursor * cursor);
	extern DECLSPEC SDL_Cursor *SDLCALL SDL_GetCursor(void);
	extern DECLSPEC SDL_Cursor *SDLCALL SDL_GetDefaultCursor(void);
	extern DECLSPEC void SDLCALL SDL_FreeCursor(SDL_Cursor * cursor);
	extern DECLSPEC int SDLCALL SDL_ShowCursor(int toggle);
### SDL_joystick.h - Joystick Support
	extern DECLSPEC void SDLCALL SDL_LockJoysticks(void);
	extern DECLSPEC void SDLCALL SDL_UnlockJoysticks(void);
	extern DECLSPEC int SDLCALL SDL_NumJoysticks(void);
	extern DECLSPEC const char *SDLCALL SDL_JoystickNameForIndex(int device_index);
	extern DECLSPEC SDL_JoystickGUID SDLCALL SDL_JoystickGetDeviceGUID(int device_index);
	extern DECLSPEC Uint16 SDLCALL SDL_JoystickGetDeviceVendor(int device_index);
	extern DECLSPEC Uint16 SDLCALL SDL_JoystickGetDeviceProduct(int device_index);
	extern DECLSPEC Uint16 SDLCALL SDL_JoystickGetDeviceProductVersion(int device_index);
	extern DECLSPEC SDL_JoystickType SDLCALL SDL_JoystickGetDeviceType(int device_index);
	extern DECLSPEC SDL_JoystickID SDLCALL SDL_JoystickGetDeviceInstanceID(int device_index);
	extern DECLSPEC SDL_Joystick *SDLCALL SDL_JoystickOpen(int device_index);
	extern DECLSPEC SDL_Joystick *SDLCALL SDL_JoystickFromInstanceID(SDL_JoystickID joyid);
	extern DECLSPEC const char *SDLCALL SDL_JoystickName(SDL_Joystick * joystick);
	extern DECLSPEC SDL_JoystickGUID SDLCALL SDL_JoystickGetGUID(SDL_Joystick * joystick);
	extern DECLSPEC Uint16 SDLCALL SDL_JoystickGetVendor(SDL_Joystick * joystick);
	extern DECLSPEC Uint16 SDLCALL SDL_JoystickGetProduct(SDL_Joystick * joystick);
	extern DECLSPEC Uint16 SDLCALL SDL_JoystickGetProductVersion(SDL_Joystick * joystick);
	extern DECLSPEC SDL_JoystickType SDLCALL SDL_JoystickGetType(SDL_Joystick * joystick);
	extern DECLSPEC void SDLCALL SDL_JoystickGetGUIDString(SDL_JoystickGUID guid, char *pszGUID, int cbGUID);
	extern DECLSPEC SDL_JoystickGUID SDLCALL SDL_JoystickGetGUIDFromString(const char *pchGUID);
	extern DECLSPEC SDL_bool SDLCALL SDL_JoystickGetAttached(SDL_Joystick * joystick);
	extern DECLSPEC SDL_JoystickID SDLCALL SDL_JoystickInstanceID(SDL_Joystick * joystick);
	extern DECLSPEC int SDLCALL SDL_JoystickNumAxes(SDL_Joystick * joystick);
	extern DECLSPEC int SDLCALL SDL_JoystickNumBalls(SDL_Joystick * joystick);
	extern DECLSPEC int SDLCALL SDL_JoystickNumHats(SDL_Joystick * joystick);
	extern DECLSPEC int SDLCALL SDL_JoystickNumButtons(SDL_Joystick * joystick);
	extern DECLSPEC void SDLCALL SDL_JoystickUpdate(void);
	extern DECLSPEC int SDLCALL SDL_JoystickEventState(int state);
	extern DECLSPEC Sint16 SDLCALL SDL_JoystickGetAxis(SDL_Joystick * joystick,
	                                                   int axis);
	extern DECLSPEC SDL_bool SDLCALL SDL_JoystickGetAxisInitialState(SDL_Joystick * joystick,
	                                                   int axis, Sint16 *state);
	extern DECLSPEC Uint8 SDLCALL SDL_JoystickGetHat(SDL_Joystick * joystick,
	                                                 int hat);
	extern DECLSPEC int SDLCALL SDL_JoystickGetBall(SDL_Joystick * joystick,
	                                                int ball, int *dx, int *dy);
	extern DECLSPEC Uint8 SDLCALL SDL_JoystickGetButton(SDL_Joystick * joystick,
	                                                    int button);
	extern DECLSPEC void SDLCALL SDL_JoystickClose(SDL_Joystick * joystick);
	extern DECLSPEC SDL_JoystickPowerLevel SDLCALL SDL_JoystickCurrentPowerLevel(SDL_Joystick * joystick);
### SDL_gamecontroller.h - Game Controller Support
	extern DECLSPEC int SDLCALL SDL_GameControllerAddMappingsFromRW(SDL_RWops * rw, int freerw);
	extern DECLSPEC int SDLCALL SDL_GameControllerAddMapping(const char* mappingString);
	extern DECLSPEC int SDLCALL SDL_GameControllerNumMappings(void);
	extern DECLSPEC char * SDLCALL SDL_GameControllerMappingForIndex(int mapping_index);
	extern DECLSPEC char * SDLCALL SDL_GameControllerMappingForGUID(SDL_JoystickGUID guid);
	extern DECLSPEC char * SDLCALL SDL_GameControllerMapping(SDL_GameController * gamecontroller);
	extern DECLSPEC SDL_bool SDLCALL SDL_IsGameController(int joystick_index);
	extern DECLSPEC const char *SDLCALL SDL_GameControllerNameForIndex(int joystick_index);
	extern DECLSPEC SDL_GameController *SDLCALL SDL_GameControllerOpen(int joystick_index);
	extern DECLSPEC SDL_GameController *SDLCALL SDL_GameControllerFromInstanceID(SDL_JoystickID joyid);
	extern DECLSPEC const char *SDLCALL SDL_GameControllerName(SDL_GameController *gamecontroller);
	extern DECLSPEC Uint16 SDLCALL SDL_GameControllerGetVendor(SDL_GameController * gamecontroller);
	extern DECLSPEC Uint16 SDLCALL SDL_GameControllerGetProduct(SDL_GameController * gamecontroller);
	extern DECLSPEC Uint16 SDLCALL SDL_GameControllerGetProductVersion(SDL_GameController * gamecontroller);
	extern DECLSPEC SDL_bool SDLCALL SDL_GameControllerGetAttached(SDL_GameController *gamecontroller);
	extern DECLSPEC SDL_Joystick *SDLCALL SDL_GameControllerGetJoystick(SDL_GameController *gamecontroller);
	extern DECLSPEC int SDLCALL SDL_GameControllerEventState(int state);
	extern DECLSPEC void SDLCALL SDL_GameControllerUpdate(void);
	extern DECLSPEC SDL_GameControllerAxis SDLCALL SDL_GameControllerGetAxisFromString(const char *pchString);
	extern DECLSPEC const char* SDLCALL SDL_GameControllerGetStringForAxis(SDL_GameControllerAxis axis);
	extern DECLSPEC SDL_GameControllerButtonBind SDLCALL
	SDL_GameControllerGetBindForAxis(SDL_GameController *gamecontroller,
	                                 SDL_GameControllerAxis axis);
	extern DECLSPEC Sint16 SDLCALL
	SDL_GameControllerGetAxis(SDL_GameController *gamecontroller,
	                          SDL_GameControllerAxis axis);
	extern DECLSPEC SDL_GameControllerButton SDLCALL SDL_GameControllerGetButtonFromString(const char *pchString);
	extern DECLSPEC const char* SDLCALL SDL_GameControllerGetStringForButton(SDL_GameControllerButton button);
	extern DECLSPEC SDL_GameControllerButtonBind SDLCALL
	SDL_GameControllerGetBindForButton(SDL_GameController *gamecontroller,
	                                   SDL_GameControllerButton button);
	extern DECLSPEC Uint8 SDLCALL SDL_GameControllerGetButton(SDL_GameController *gamecontroller,
	                                                          SDL_GameControllerButton button);
	extern DECLSPEC void SDLCALL SDL_GameControllerClose(SDL_GameController *gamecontroller);
## Force Feedback
### SDL_haptic.h - Force Feedback Support
	extern DECLSPEC int SDLCALL SDL_NumHaptics(void);
	extern DECLSPEC const char *SDLCALL SDL_HapticName(int device_index);
	extern DECLSPEC SDL_Haptic *SDLCALL SDL_HapticOpen(int device_index);
	extern DECLSPEC int SDLCALL SDL_HapticOpened(int device_index);
	extern DECLSPEC int SDLCALL SDL_HapticIndex(SDL_Haptic * haptic);
	extern DECLSPEC int SDLCALL SDL_MouseIsHaptic(void);
	extern DECLSPEC SDL_Haptic *SDLCALL SDL_HapticOpenFromMouse(void);
	extern DECLSPEC int SDLCALL SDL_JoystickIsHaptic(SDL_Joystick * joystick);
	extern DECLSPEC SDL_Haptic *SDLCALL SDL_HapticOpenFromJoystick(SDL_Joystick *
	                                                               joystick);
	extern DECLSPEC void SDLCALL SDL_HapticClose(SDL_Haptic * haptic);
	extern DECLSPEC int SDLCALL SDL_HapticNumEffects(SDL_Haptic * haptic);
	extern DECLSPEC int SDLCALL SDL_HapticNumEffectsPlaying(SDL_Haptic * haptic);
	extern DECLSPEC unsigned int SDLCALL SDL_HapticQuery(SDL_Haptic * haptic);
	extern DECLSPEC int SDLCALL SDL_HapticNumAxes(SDL_Haptic * haptic);
	extern DECLSPEC int SDLCALL SDL_HapticEffectSupported(SDL_Haptic * haptic,
	                                                      SDL_HapticEffect *
	                                                      effect);
	extern DECLSPEC int SDLCALL SDL_HapticNewEffect(SDL_Haptic * haptic,
	                                                SDL_HapticEffect * effect);
	extern DECLSPEC int SDLCALL SDL_HapticUpdateEffect(SDL_Haptic * haptic,
	                                                   int effect,
	                                                   SDL_HapticEffect * data);
	extern DECLSPEC int SDLCALL SDL_HapticRunEffect(SDL_Haptic * haptic,
	                                                int effect,
	                                                Uint32 iterations);
	extern DECLSPEC int SDLCALL SDL_HapticStopEffect(SDL_Haptic * haptic,
	                                                 int effect);
	extern DECLSPEC void SDLCALL SDL_HapticDestroyEffect(SDL_Haptic * haptic,
	                                                     int effect);
	extern DECLSPEC int SDLCALL SDL_HapticGetEffectStatus(SDL_Haptic * haptic,
	                                                      int effect);
	extern DECLSPEC int SDLCALL SDL_HapticSetGain(SDL_Haptic * haptic, int gain);
	extern DECLSPEC int SDLCALL SDL_HapticSetAutocenter(SDL_Haptic * haptic,
	                                                    int autocenter);
	extern DECLSPEC int SDLCALL SDL_HapticPause(SDL_Haptic * haptic);
	extern DECLSPEC int SDLCALL SDL_HapticUnpause(SDL_Haptic * haptic);
	extern DECLSPEC int SDLCALL SDL_HapticStopAll(SDL_Haptic * haptic);
	extern DECLSPEC int SDLCALL SDL_HapticRumbleSupported(SDL_Haptic * haptic);
	extern DECLSPEC int SDLCALL SDL_HapticRumbleInit(SDL_Haptic * haptic);
	extern DECLSPEC int SDLCALL SDL_HapticRumblePlay(SDL_Haptic * haptic, float strength, Uint32 length );
	extern DECLSPEC int SDLCALL SDL_HapticRumbleStop(SDL_Haptic * haptic);
## Audio
### SDL_audio.h - Audio Device Management, Playing and Recording
	extern DECLSPEC int SDLCALL SDL_GetNumAudioDrivers(void);
	extern DECLSPEC const char *SDLCALL SDL_GetAudioDriver(int index);
	extern DECLSPEC int SDLCALL SDL_AudioInit(const char *driver_name);
	extern DECLSPEC void SDLCALL SDL_AudioQuit(void);
	extern DECLSPEC const char *SDLCALL SDL_GetCurrentAudioDriver(void);
	extern DECLSPEC int SDLCALL SDL_OpenAudio(SDL_AudioSpec * desired,
	                                          SDL_AudioSpec * obtained);
	extern DECLSPEC int SDLCALL SDL_GetNumAudioDevices(int iscapture);
	extern DECLSPEC const char *SDLCALL SDL_GetAudioDeviceName(int index,
	                                                           int iscapture);
	extern DECLSPEC SDL_AudioDeviceID SDLCALL SDL_OpenAudioDevice(const char
	                                                              *device,
	                                                              int iscapture,
	                                                              const
	                                                              SDL_AudioSpec *
	                                                              desired,
	                                                              SDL_AudioSpec *
	                                                              obtained,
	                                                              int
	                                                              allowed_changes);
	extern DECLSPEC SDL_AudioStatus SDLCALL SDL_GetAudioStatus(void);
	extern DECLSPEC SDL_AudioStatus SDLCALL
	SDL_GetAudioDeviceStatus(SDL_AudioDeviceID dev);
	extern DECLSPEC void SDLCALL SDL_PauseAudio(int pause_on);
	extern DECLSPEC void SDLCALL SDL_PauseAudioDevice(SDL_AudioDeviceID dev,
	                                                  int pause_on);
	extern DECLSPEC SDL_AudioSpec *SDLCALL SDL_LoadWAV_RW(SDL_RWops * src,
	                                                      int freesrc,
	                                                      SDL_AudioSpec * spec,
	                                                      Uint8 ** audio_buf,
	                                                      Uint32 * audio_len);
	extern DECLSPEC void SDLCALL SDL_FreeWAV(Uint8 * audio_buf);
	extern DECLSPEC int SDLCALL SDL_BuildAudioCVT(SDL_AudioCVT * cvt,
	                                              SDL_AudioFormat src_format,
	                                              Uint8 src_channels,
	                                              int src_rate,
	                                              SDL_AudioFormat dst_format,
	                                              Uint8 dst_channels,
	                                              int dst_rate);
	extern DECLSPEC int SDLCALL SDL_ConvertAudio(SDL_AudioCVT * cvt);
	extern DECLSPEC SDL_AudioStream * SDLCALL SDL_NewAudioStream(const SDL_AudioFormat src_format,
	                                           const Uint8 src_channels,
	                                           const int src_rate,
	                                           const SDL_AudioFormat dst_format,
	                                           const Uint8 dst_channels,
	                                           const int dst_rate);
	extern DECLSPEC int SDLCALL SDL_AudioStreamPut(SDL_AudioStream *stream, const void *buf, int len);
	extern DECLSPEC int SDLCALL SDL_AudioStreamGet(SDL_AudioStream *stream, void *buf, int len);
	extern DECLSPEC int SDLCALL SDL_AudioStreamAvailable(SDL_AudioStream *stream);
	extern DECLSPEC int SDLCALL SDL_AudioStreamFlush(SDL_AudioStream *stream);
	extern DECLSPEC void SDLCALL SDL_AudioStreamClear(SDL_AudioStream *stream);
	extern DECLSPEC void SDLCALL SDL_FreeAudioStream(SDL_AudioStream *stream);
	extern DECLSPEC void SDLCALL SDL_MixAudio(Uint8 * dst, const Uint8 * src,
	                                          Uint32 len, int volume);
	extern DECLSPEC void SDLCALL SDL_MixAudioFormat(Uint8 * dst,
	                                                const Uint8 * src,
	                                                SDL_AudioFormat format,
	                                                Uint32 len, int volume);
	extern DECLSPEC int SDLCALL SDL_QueueAudio(SDL_AudioDeviceID dev, const void *data, Uint32 len);
	extern DECLSPEC Uint32 SDLCALL SDL_DequeueAudio(SDL_AudioDeviceID dev, void *data, Uint32 len);
	extern DECLSPEC Uint32 SDLCALL SDL_GetQueuedAudioSize(SDL_AudioDeviceID dev);
	extern DECLSPEC void SDLCALL SDL_ClearQueuedAudio(SDL_AudioDeviceID dev);
	extern DECLSPEC void SDLCALL SDL_LockAudio(void);
	extern DECLSPEC void SDLCALL SDL_LockAudioDevice(SDL_AudioDeviceID dev);
	extern DECLSPEC void SDLCALL SDL_UnlockAudio(void);
	extern DECLSPEC void SDLCALL SDL_UnlockAudioDevice(SDL_AudioDeviceID dev);
	extern DECLSPEC void SDLCALL SDL_CloseAudio(void);
	extern DECLSPEC void SDLCALL SDL_CloseAudioDevice(SDL_AudioDeviceID dev);
## Threads
### SDL_thread.h - Thread Management
	extern DECLSPEC SDL_Thread *SDLCALL
	SDL_CreateThread(SDL_ThreadFunction fn, const char *name, void *data,
	                 pfnSDL_CurrentBeginThread pfnBeginThread,
	                 pfnSDL_CurrentEndThread pfnEndThread);
	extern DECLSPEC SDL_Thread *SDLCALL
	SDL_CreateThread(SDL_ThreadFunction fn, const char *name, void *data);
	extern DECLSPEC const char *SDLCALL SDL_GetThreadName(SDL_Thread *thread);
	extern DECLSPEC SDL_threadID SDLCALL SDL_ThreadID(void);
	extern DECLSPEC SDL_threadID SDLCALL SDL_GetThreadID(SDL_Thread * thread);
	extern DECLSPEC int SDLCALL SDL_SetThreadPriority(SDL_ThreadPriority priority);
	extern DECLSPEC void SDLCALL SDL_WaitThread(SDL_Thread * thread, int *status);
	extern DECLSPEC void SDLCALL SDL_DetachThread(SDL_Thread * thread);
	extern DECLSPEC SDL_TLSID SDLCALL SDL_TLSCreate(void);
	extern DECLSPEC void * SDLCALL SDL_TLSGet(SDL_TLSID id);
	extern DECLSPEC int SDLCALL SDL_TLSSet(SDL_TLSID id, const void *value, void (SDLCALL *destructor)(void*));
### SDL_mutex.h - Thread Synchronization Primitives
	extern DECLSPEC SDL_mutex *SDLCALL SDL_CreateMutex(void);
	extern DECLSPEC int SDLCALL SDL_LockMutex(SDL_mutex * mutex);
	extern DECLSPEC int SDLCALL SDL_TryLockMutex(SDL_mutex * mutex);
	extern DECLSPEC int SDLCALL SDL_UnlockMutex(SDL_mutex * mutex);
	extern DECLSPEC void SDLCALL SDL_DestroyMutex(SDL_mutex * mutex);
	extern DECLSPEC SDL_sem *SDLCALL SDL_CreateSemaphore(Uint32 initial_value);
	extern DECLSPEC void SDLCALL SDL_DestroySemaphore(SDL_sem * sem);
	extern DECLSPEC int SDLCALL SDL_SemWait(SDL_sem * sem);
	extern DECLSPEC int SDLCALL SDL_SemTryWait(SDL_sem * sem);
	extern DECLSPEC int SDLCALL SDL_SemWaitTimeout(SDL_sem * sem, Uint32 ms);
	extern DECLSPEC int SDLCALL SDL_SemPost(SDL_sem * sem);
	extern DECLSPEC Uint32 SDLCALL SDL_SemValue(SDL_sem * sem);
	extern DECLSPEC SDL_cond *SDLCALL SDL_CreateCond(void);
	extern DECLSPEC void SDLCALL SDL_DestroyCond(SDL_cond * cond);
	extern DECLSPEC int SDLCALL SDL_CondSignal(SDL_cond * cond);
	extern DECLSPEC int SDLCALL SDL_CondBroadcast(SDL_cond * cond);
	extern DECLSPEC int SDLCALL SDL_CondWait(SDL_cond * cond, SDL_mutex * mutex);
	extern DECLSPEC int SDLCALL SDL_CondWaitTimeout(SDL_cond * cond,
	                                                SDL_mutex * mutex, Uint32 ms);
### SDL_atomic.h - Atomic Operations
	extern DECLSPEC SDL_bool SDLCALL SDL_AtomicTryLock(SDL_SpinLock *lock);
	extern DECLSPEC void SDLCALL SDL_AtomicLock(SDL_SpinLock *lock);
	extern DECLSPEC void SDLCALL SDL_AtomicUnlock(SDL_SpinLock *lock);
	extern DECLSPEC void SDLCALL SDL_MemoryBarrierReleaseFunction(void);
	extern DECLSPEC void SDLCALL SDL_MemoryBarrierAcquireFunction(void);
	extern DECLSPEC SDL_bool SDLCALL SDL_AtomicCAS(SDL_atomic_t *a, int oldval, int newval);
	extern DECLSPEC int SDLCALL SDL_AtomicSet(SDL_atomic_t *a, int v);
	extern DECLSPEC int SDLCALL SDL_AtomicGet(SDL_atomic_t *a);
	extern DECLSPEC int SDLCALL SDL_AtomicAdd(SDL_atomic_t *a, int v);
	extern DECLSPEC SDL_bool SDLCALL SDL_AtomicCASPtr(void **a, void *oldval, void *newval);
	extern DECLSPEC void* SDLCALL SDL_AtomicSetPtr(void **a, void* v);
	extern DECLSPEC void* SDLCALL SDL_AtomicGetPtr(void **a);
## Timers
### SDL_timer.h - Timer Support
	extern DECLSPEC Uint32 SDLCALL SDL_GetTicks(void);
	extern DECLSPEC Uint64 SDLCALL SDL_GetPerformanceCounter(void);
	extern DECLSPEC Uint64 SDLCALL SDL_GetPerformanceFrequency(void);
	extern DECLSPEC void SDLCALL SDL_Delay(Uint32 ms);
	extern DECLSPEC SDL_TimerID SDLCALL SDL_AddTimer(Uint32 interval,
	                                                 SDL_TimerCallback callback,
	                                                 void *param);
	extern DECLSPEC SDL_bool SDLCALL SDL_RemoveTimer(SDL_TimerID id);
## File Abstraction
### SDL_filesystem.h - Filesystem Paths
	extern DECLSPEC char *SDLCALL SDL_GetBasePath(void);
	extern DECLSPEC char *SDLCALL SDL_GetPrefPath(const char *org, const char *app);
### SDL_rwops.h - File I/O Abstraction
	extern DECLSPEC SDL_RWops *SDLCALL SDL_RWFromFile(const char *file,
	                                                  const char *mode);
	extern DECLSPEC SDL_RWops *SDLCALL SDL_RWFromFP(FILE * fp,
	                                                SDL_bool autoclose);
	extern DECLSPEC SDL_RWops *SDLCALL SDL_RWFromFP(void * fp,
	                                                SDL_bool autoclose);
	extern DECLSPEC SDL_RWops *SDLCALL SDL_RWFromMem(void *mem, int size);
	extern DECLSPEC SDL_RWops *SDLCALL SDL_RWFromConstMem(const void *mem,
	                                                      int size);
	extern DECLSPEC SDL_RWops *SDLCALL SDL_AllocRW(void);
	extern DECLSPEC void SDLCALL SDL_FreeRW(SDL_RWops * area);
	extern DECLSPEC void *SDLCALL SDL_LoadFile_RW(SDL_RWops * src, size_t *datasize,
	                                                    int freesrc);
	extern DECLSPEC Uint8 SDLCALL SDL_ReadU8(SDL_RWops * src);
	extern DECLSPEC Uint16 SDLCALL SDL_ReadLE16(SDL_RWops * src);
	extern DECLSPEC Uint16 SDLCALL SDL_ReadBE16(SDL_RWops * src);
	extern DECLSPEC Uint32 SDLCALL SDL_ReadLE32(SDL_RWops * src);
	extern DECLSPEC Uint32 SDLCALL SDL_ReadBE32(SDL_RWops * src);
	extern DECLSPEC Uint64 SDLCALL SDL_ReadLE64(SDL_RWops * src);
	extern DECLSPEC Uint64 SDLCALL SDL_ReadBE64(SDL_RWops * src);
	extern DECLSPEC size_t SDLCALL SDL_WriteU8(SDL_RWops * dst, Uint8 value);
	extern DECLSPEC size_t SDLCALL SDL_WriteLE16(SDL_RWops * dst, Uint16 value);
	extern DECLSPEC size_t SDLCALL SDL_WriteBE16(SDL_RWops * dst, Uint16 value);
	extern DECLSPEC size_t SDLCALL SDL_WriteLE32(SDL_RWops * dst, Uint32 value);
	extern DECLSPEC size_t SDLCALL SDL_WriteBE32(SDL_RWops * dst, Uint32 value);
	extern DECLSPEC size_t SDLCALL SDL_WriteLE64(SDL_RWops * dst, Uint64 value);
	extern DECLSPEC size_t SDLCALL SDL_WriteBE64(SDL_RWops * dst, Uint64 value);
## Shared Object Support
### SDL_loadso.h - Shared Object Loading and Function Lookup
	extern DECLSPEC void *SDLCALL SDL_LoadObject(const char *sofile);
	extern DECLSPEC void *SDLCALL SDL_LoadFunction(void *handle,
	                                               const char *name);
	extern DECLSPEC void SDLCALL SDL_UnloadObject(void *handle);
## Platform and CPU Information
### SDL_platform.h - Platform Detection
	extern DECLSPEC const char * SDLCALL SDL_GetPlatform (void);
### SDL_cpuinfo.h - CPU Feature Detection
	extern DECLSPEC int SDLCALL SDL_GetCPUCount(void);
	extern DECLSPEC int SDLCALL SDL_GetCPUCacheLineSize(void);
	extern DECLSPEC SDL_bool SDLCALL SDL_HasRDTSC(void);
	extern DECLSPEC SDL_bool SDLCALL SDL_HasAltiVec(void);
	extern DECLSPEC SDL_bool SDLCALL SDL_HasMMX(void);
	extern DECLSPEC SDL_bool SDLCALL SDL_Has3DNow(void);
	extern DECLSPEC SDL_bool SDLCALL SDL_HasSSE(void);
	extern DECLSPEC SDL_bool SDLCALL SDL_HasSSE2(void);
	extern DECLSPEC SDL_bool SDLCALL SDL_HasSSE3(void);
	extern DECLSPEC SDL_bool SDLCALL SDL_HasSSE41(void);
	extern DECLSPEC SDL_bool SDLCALL SDL_HasSSE42(void);
	extern DECLSPEC SDL_bool SDLCALL SDL_HasAVX(void);
	extern DECLSPEC SDL_bool SDLCALL SDL_HasAVX2(void);
	extern DECLSPEC SDL_bool SDLCALL SDL_HasNEON(void);
	extern DECLSPEC int SDLCALL SDL_GetSystemRAM(void);
### SDL_endian.h - Byte Order and Byte Swapping
	SDL_FORCE_INLINE Uint16 SDL_Swap16(Uint16 x);
	SDL_FORCE_INLINE Uint32 SDL_Swap32(Uint32 x);
	SDL_FORCE_INLINE Uint64 SDL_Swap64(Uint64 x);
	SDL_FORCE_INLINE float SDL_SwapFloat(float x);
### SDL_bits.h - Bit Manipulation
	SDL_FORCE_INLINE int SDL_MostSignificantBitIndex32(Uint32 x);
## Power Management
### SDL_power.h - Power Management Status
	extern DECLSPEC SDL_PowerState SDLCALL SDL_GetPowerInfo(int *secs, int *pct);
## Additional Functionality
### SDL_system.h - Platform-specific Functionality
	extern DECLSPEC void SDLCALL SDL_SetWindowsMessageHook(SDL_WindowsMessageHook callback, void *userdata);
	extern DECLSPEC int SDLCALL SDL_Direct3D9GetAdapterIndex( int displayIndex );
	extern DECLSPEC IDirect3DDevice9* SDLCALL SDL_RenderGetD3D9Device(SDL_Renderer * renderer);
	extern DECLSPEC SDL_bool SDLCALL SDL_DXGIGetOutputInfo( int displayIndex, int *adapterIndex, int *outputIndex );
	extern DECLSPEC int SDLCALL SDL_iPhoneSetAnimationCallback(SDL_Window * window, int interval, void (*callback)(void*), void *callbackParam);
	extern DECLSPEC void SDLCALL SDL_iPhoneSetEventPump(SDL_bool enabled);
	extern DECLSPEC void * SDLCALL SDL_AndroidGetJNIEnv(void);
	extern DECLSPEC void * SDLCALL SDL_AndroidGetActivity(void);
	extern DECLSPEC const char * SDLCALL SDL_AndroidGetInternalStoragePath(void);
	extern DECLSPEC int SDLCALL SDL_AndroidGetExternalStorageState(void);
	extern DECLSPEC const char * SDLCALL SDL_AndroidGetExternalStoragePath(void);
	extern DECLSPEC const wchar_t * SDLCALL SDL_WinRTGetFSPathUNICODE(SDL_WinRT_Path pathType);
	extern DECLSPEC const char * SDLCALL SDL_WinRTGetFSPathUTF8(SDL_WinRT_Path pathType);
### SDL_stdinc.h - Standard Library Functionality
	extern DECLSPEC void *SDLCALL SDL_malloc(size_t size);
	extern DECLSPEC void *SDLCALL SDL_calloc(size_t nmemb, size_t size);
	extern DECLSPEC void *SDLCALL SDL_realloc(void *mem, size_t size);
	extern DECLSPEC void SDLCALL SDL_free(void *mem);
	extern DECLSPEC void SDLCALL SDL_GetMemoryFunctions(SDL_malloc_func *malloc_func,
	                                                    SDL_calloc_func *calloc_func,
	                                                    SDL_realloc_func *realloc_func,
	                                                    SDL_free_func *free_func);
	extern DECLSPEC int SDLCALL SDL_SetMemoryFunctions(SDL_malloc_func malloc_func,
	                                                   SDL_calloc_func calloc_func,
	                                                   SDL_realloc_func realloc_func,
	                                                   SDL_free_func free_func);
	extern DECLSPEC int SDLCALL SDL_GetNumAllocations(void);
	extern DECLSPEC char *SDLCALL SDL_getenv(const char *name);
	extern DECLSPEC int SDLCALL SDL_setenv(const char *name, const char *value, int overwrite);
	extern DECLSPEC void SDLCALL SDL_qsort(void *base, size_t nmemb, size_t size, int (*compare) (const void *, const void *));
	extern DECLSPEC int SDLCALL SDL_abs(int x);
	extern DECLSPEC int SDLCALL SDL_isdigit(int x);
	extern DECLSPEC int SDLCALL SDL_isspace(int x);
	extern DECLSPEC int SDLCALL SDL_toupper(int x);
	extern DECLSPEC int SDLCALL SDL_tolower(int x);
	extern DECLSPEC void *SDLCALL SDL_memset(SDL_OUT_BYTECAP(len) void *dst, int c, size_t len);
	extern DECLSPEC void *SDLCALL SDL_memcpy(SDL_OUT_BYTECAP(len) void *dst, SDL_IN_BYTECAP(len) const void *src, size_t len);
	extern DECLSPEC void *SDLCALL SDL_memmove(SDL_OUT_BYTECAP(len) void *dst, SDL_IN_BYTECAP(len) const void *src, size_t len);
	extern DECLSPEC int SDLCALL SDL_memcmp(const void *s1, const void *s2, size_t len);
	extern DECLSPEC size_t SDLCALL SDL_wcslen(const wchar_t *wstr);
	extern DECLSPEC size_t SDLCALL SDL_wcslcpy(SDL_OUT_Z_CAP(maxlen) wchar_t *dst, const wchar_t *src, size_t maxlen);
	extern DECLSPEC size_t SDLCALL SDL_wcslcat(SDL_INOUT_Z_CAP(maxlen) wchar_t *dst, const wchar_t *src, size_t maxlen);
	extern DECLSPEC int SDLCALL SDL_wcscmp(const wchar_t *str1, const wchar_t *str2);
	extern DECLSPEC size_t SDLCALL SDL_strlen(const char *str);
	extern DECLSPEC size_t SDLCALL SDL_strlcpy(SDL_OUT_Z_CAP(maxlen) char *dst, const char *src, size_t maxlen);
	extern DECLSPEC size_t SDLCALL SDL_utf8strlcpy(SDL_OUT_Z_CAP(dst_bytes) char *dst, const char *src, size_t dst_bytes);
	extern DECLSPEC size_t SDLCALL SDL_strlcat(SDL_INOUT_Z_CAP(maxlen) char *dst, const char *src, size_t maxlen);
	extern DECLSPEC char *SDLCALL SDL_strdup(const char *str);
	extern DECLSPEC char *SDLCALL SDL_strrev(char *str);
	extern DECLSPEC char *SDLCALL SDL_strupr(char *str);
	extern DECLSPEC char *SDLCALL SDL_strlwr(char *str);
	extern DECLSPEC char *SDLCALL SDL_strchr(const char *str, int c);
	extern DECLSPEC char *SDLCALL SDL_strrchr(const char *str, int c);
	extern DECLSPEC char *SDLCALL SDL_strstr(const char *haystack, const char *needle);
	extern DECLSPEC size_t SDLCALL SDL_utf8strlen(const char *str);
	extern DECLSPEC char *SDLCALL SDL_itoa(int value, char *str, int radix);
	extern DECLSPEC char *SDLCALL SDL_uitoa(unsigned int value, char *str, int radix);
	extern DECLSPEC char *SDLCALL SDL_ltoa(long value, char *str, int radix);
	extern DECLSPEC char *SDLCALL SDL_ultoa(unsigned long value, char *str, int radix);
	extern DECLSPEC char *SDLCALL SDL_lltoa(Sint64 value, char *str, int radix);
	extern DECLSPEC char *SDLCALL SDL_ulltoa(Uint64 value, char *str, int radix);
	extern DECLSPEC int SDLCALL SDL_atoi(const char *str);
	extern DECLSPEC double SDLCALL SDL_atof(const char *str);
	extern DECLSPEC long SDLCALL SDL_strtol(const char *str, char **endp, int base);
	extern DECLSPEC unsigned long SDLCALL SDL_strtoul(const char *str, char **endp, int base);
	extern DECLSPEC Sint64 SDLCALL SDL_strtoll(const char *str, char **endp, int base);
	extern DECLSPEC Uint64 SDLCALL SDL_strtoull(const char *str, char **endp, int base);
	extern DECLSPEC double SDLCALL SDL_strtod(const char *str, char **endp);
	extern DECLSPEC int SDLCALL SDL_strcmp(const char *str1, const char *str2);
	extern DECLSPEC int SDLCALL SDL_strncmp(const char *str1, const char *str2, size_t maxlen);
	extern DECLSPEC int SDLCALL SDL_strcasecmp(const char *str1, const char *str2);
	extern DECLSPEC int SDLCALL SDL_strncasecmp(const char *str1, const char *str2, size_t len);
	extern DECLSPEC int SDLCALL SDL_sscanf(const char *text, SDL_SCANF_FORMAT_STRING const char *fmt, ...) SDL_SCANF_VARARG_FUNC(2);
	extern DECLSPEC int SDLCALL SDL_vsscanf(const char *text, const char *fmt, va_list ap);
	extern DECLSPEC int SDLCALL SDL_snprintf(SDL_OUT_Z_CAP(maxlen) char *text, size_t maxlen, SDL_PRINTF_FORMAT_STRING const char *fmt, ... ) SDL_PRINTF_VARARG_FUNC(3);
	extern DECLSPEC int SDLCALL SDL_vsnprintf(SDL_OUT_Z_CAP(maxlen) char *text, size_t maxlen, const char *fmt, va_list ap);
	extern DECLSPEC double SDLCALL SDL_acos(double x);
	extern DECLSPEC double SDLCALL SDL_asin(double x);
	extern DECLSPEC double SDLCALL SDL_atan(double x);
	extern DECLSPEC double SDLCALL SDL_atan2(double x, double y);
	extern DECLSPEC double SDLCALL SDL_ceil(double x);
	extern DECLSPEC double SDLCALL SDL_copysign(double x, double y);
	extern DECLSPEC double SDLCALL SDL_cos(double x);
	extern DECLSPEC float SDLCALL SDL_cosf(float x);
	extern DECLSPEC double SDLCALL SDL_fabs(double x);
	extern DECLSPEC double SDLCALL SDL_floor(double x);
	extern DECLSPEC double SDLCALL SDL_log(double x);
	extern DECLSPEC double SDLCALL SDL_pow(double x, double y);
	extern DECLSPEC double SDLCALL SDL_scalbn(double x, int n);
	extern DECLSPEC double SDLCALL SDL_sin(double x);
	extern DECLSPEC float SDLCALL SDL_sinf(float x);
	extern DECLSPEC double SDLCALL SDL_sqrt(double x);
	extern DECLSPEC float SDLCALL SDL_sqrtf(float x);
	extern DECLSPEC double SDLCALL SDL_tan(double x);
	extern DECLSPEC float SDLCALL SDL_tanf(float x);
	extern DECLSPEC SDL_iconv_t SDLCALL SDL_iconv_open(const char *tocode,
	                                                   const char *fromcode);
	extern DECLSPEC int SDLCALL SDL_iconv_close(SDL_iconv_t cd);
	extern DECLSPEC size_t SDLCALL SDL_iconv(SDL_iconv_t cd, const char **inbuf,
	                                         size_t * inbytesleft, char **outbuf,
	                                         size_t * outbytesleft);
	extern DECLSPEC char *SDLCALL SDL_iconv_string(const char *tocode,
	                                               const char *fromcode,
	                                               const char *inbuf,
	                                               size_t inbytesleft);
## Others
### SDL_blendmode.h
	extern DECLSPEC SDL_BlendMode SDLCALL SDL_ComposeCustomBlendMode(SDL_BlendFactor srcColorFactor,
	                                                                 SDL_BlendFactor dstColorFactor,
	                                                                 SDL_BlendOperation colorOperation,
	                                                                 SDL_BlendFactor srcAlphaFactor,
	                                                                 SDL_BlendFactor dstAlphaFactor,
	                                                                 SDL_BlendOperation alphaOperation);
### SDL_gesture.h
	extern DECLSPEC int SDLCALL SDL_RecordGesture(SDL_TouchID touchId);
	extern DECLSPEC int SDLCALL SDL_SaveAllDollarTemplates(SDL_RWops *dst);
	extern DECLSPEC int SDLCALL SDL_SaveDollarTemplate(SDL_GestureID gestureId,SDL_RWops *dst);
	extern DECLSPEC int SDLCALL SDL_LoadDollarTemplates(SDL_TouchID touchId, SDL_RWops *src);
### SDL_image.h
	extern DECLSPEC const SDL_version * SDLCALL IMG_Linked_Version(void);
	extern DECLSPEC int SDLCALL IMG_Init(int flags);
	extern DECLSPEC void SDLCALL IMG_Quit(void);
	extern DECLSPEC SDL_Surface * SDLCALL IMG_LoadTyped_RW(SDL_RWops *src, int freesrc, const char *type);
	extern DECLSPEC SDL_Surface * SDLCALL IMG_Load(const char *file);
	extern DECLSPEC SDL_Surface * SDLCALL IMG_Load_RW(SDL_RWops *src, int freesrc);
	extern DECLSPEC SDL_Texture * SDLCALL IMG_LoadTexture(SDL_Renderer *renderer, const char *file);
	extern DECLSPEC SDL_Texture * SDLCALL IMG_LoadTexture_RW(SDL_Renderer *renderer, SDL_RWops *src, int freesrc);
	extern DECLSPEC SDL_Texture * SDLCALL IMG_LoadTextureTyped_RW(SDL_Renderer *renderer, SDL_RWops *src, int freesrc, const char *type);
	extern DECLSPEC int SDLCALL IMG_isICO(SDL_RWops *src);
	extern DECLSPEC int SDLCALL IMG_isCUR(SDL_RWops *src);
	extern DECLSPEC int SDLCALL IMG_isBMP(SDL_RWops *src);
	extern DECLSPEC int SDLCALL IMG_isGIF(SDL_RWops *src);
	extern DECLSPEC int SDLCALL IMG_isJPG(SDL_RWops *src);
	extern DECLSPEC int SDLCALL IMG_isLBM(SDL_RWops *src);
	extern DECLSPEC int SDLCALL IMG_isPCX(SDL_RWops *src);
	extern DECLSPEC int SDLCALL IMG_isPNG(SDL_RWops *src);
	extern DECLSPEC int SDLCALL IMG_isPNM(SDL_RWops *src);
	extern DECLSPEC int SDLCALL IMG_isSVG(SDL_RWops *src);
	extern DECLSPEC int SDLCALL IMG_isTIF(SDL_RWops *src);
	extern DECLSPEC int SDLCALL IMG_isXCF(SDL_RWops *src);
	extern DECLSPEC int SDLCALL IMG_isXPM(SDL_RWops *src);
	extern DECLSPEC int SDLCALL IMG_isXV(SDL_RWops *src);
	extern DECLSPEC int SDLCALL IMG_isWEBP(SDL_RWops *src);
	extern DECLSPEC SDL_Surface * SDLCALL IMG_LoadICO_RW(SDL_RWops *src);
	extern DECLSPEC SDL_Surface * SDLCALL IMG_LoadCUR_RW(SDL_RWops *src);
	extern DECLSPEC SDL_Surface * SDLCALL IMG_LoadBMP_RW(SDL_RWops *src);
	extern DECLSPEC SDL_Surface * SDLCALL IMG_LoadGIF_RW(SDL_RWops *src);
	extern DECLSPEC SDL_Surface * SDLCALL IMG_LoadJPG_RW(SDL_RWops *src);
	extern DECLSPEC SDL_Surface * SDLCALL IMG_LoadLBM_RW(SDL_RWops *src);
	extern DECLSPEC SDL_Surface * SDLCALL IMG_LoadPCX_RW(SDL_RWops *src);
	extern DECLSPEC SDL_Surface * SDLCALL IMG_LoadPNG_RW(SDL_RWops *src);
	extern DECLSPEC SDL_Surface * SDLCALL IMG_LoadPNM_RW(SDL_RWops *src);
	extern DECLSPEC SDL_Surface * SDLCALL IMG_LoadSVG_RW(SDL_RWops *src);
	extern DECLSPEC SDL_Surface * SDLCALL IMG_LoadTGA_RW(SDL_RWops *src);
	extern DECLSPEC SDL_Surface * SDLCALL IMG_LoadTIF_RW(SDL_RWops *src);
	extern DECLSPEC SDL_Surface * SDLCALL IMG_LoadXCF_RW(SDL_RWops *src);
	extern DECLSPEC SDL_Surface * SDLCALL IMG_LoadXPM_RW(SDL_RWops *src);
	extern DECLSPEC SDL_Surface * SDLCALL IMG_LoadXV_RW(SDL_RWops *src);
	extern DECLSPEC SDL_Surface * SDLCALL IMG_LoadWEBP_RW(SDL_RWops *src);
	extern DECLSPEC SDL_Surface * SDLCALL IMG_ReadXPMFromArray(char **xpm);
	extern DECLSPEC int SDLCALL IMG_SavePNG(SDL_Surface *surface, const char *file);
	extern DECLSPEC int SDLCALL IMG_SavePNG_RW(SDL_Surface *surface, SDL_RWops *dst, int freedst);
	extern DECLSPEC int SDLCALL IMG_SaveJPG(SDL_Surface *surface, const char *file, int quality);
	extern DECLSPEC int SDLCALL IMG_SaveJPG_RW(SDL_Surface *surface, SDL_RWops *dst, int freedst, int quality);
### SDL_main.h
	extern C_LINKAGE DECLSPEC int SDL_main(int argc, char *argv[]);
	extern DECLSPEC void SDLCALL SDL_SetMainReady(void);
	extern DECLSPEC int SDLCALL SDL_RegisterApp(char *name, Uint32 style,
	                                            void *hInst);
	extern DECLSPEC void SDLCALL SDL_UnregisterApp(void);
	extern DECLSPEC int SDLCALL SDL_WinRTRunApp(int (*mainFunction)(int, char **), void * reserved);
### SDL_messagebox.h
	extern DECLSPEC int SDLCALL SDL_ShowMessageBox(const SDL_MessageBoxData *messageboxdata, int *buttonid);
	extern DECLSPEC int SDLCALL SDL_ShowSimpleMessageBox(Uint32 flags, const char *title, const char *message, SDL_Window *window);
### SDL_mixer.h
	extern DECLSPEC const SDL_version * SDLCALL Mix_Linked_Version(void);
	extern DECLSPEC int SDLCALL Mix_Init(int flags);
	extern DECLSPEC void SDLCALL Mix_Quit(void);
	extern DECLSPEC int SDLCALL Mix_OpenAudio(int frequency, Uint16 format, int channels, int chunksize);
	extern DECLSPEC int SDLCALL Mix_OpenAudioDevice(int frequency, Uint16 format, int channels, int chunksize, const char* device, int allowed_changes);
	extern DECLSPEC int SDLCALL Mix_AllocateChannels(int numchans);
	extern DECLSPEC int SDLCALL Mix_QuerySpec(int *frequency,Uint16 *format,int *channels);
	extern DECLSPEC Mix_Chunk * SDLCALL Mix_LoadWAV_RW(SDL_RWops *src, int freesrc);
	extern DECLSPEC Mix_Music * SDLCALL Mix_LoadMUS(const char *file);
	extern DECLSPEC Mix_Music * SDLCALL Mix_LoadMUS_RW(SDL_RWops *src, int freesrc);
	extern DECLSPEC Mix_Music * SDLCALL Mix_LoadMUSType_RW(SDL_RWops *src, Mix_MusicType type, int freesrc);
	extern DECLSPEC Mix_Chunk * SDLCALL Mix_QuickLoad_WAV(Uint8 *mem);
	extern DECLSPEC Mix_Chunk * SDLCALL Mix_QuickLoad_RAW(Uint8 *mem, Uint32 len);
	extern DECLSPEC void SDLCALL Mix_FreeChunk(Mix_Chunk *chunk);
	extern DECLSPEC void SDLCALL Mix_FreeMusic(Mix_Music *music);
	extern DECLSPEC int SDLCALL Mix_GetNumChunkDecoders(void);
	extern DECLSPEC const char * SDLCALL Mix_GetChunkDecoder(int index);
	extern DECLSPEC SDL_bool SDLCALL Mix_HasChunkDecoder(const char *name);
	extern DECLSPEC int SDLCALL Mix_GetNumMusicDecoders(void);
	extern DECLSPEC const char * SDLCALL Mix_GetMusicDecoder(int index);
	extern DECLSPEC SDL_bool SDLCALL Mix_HasMusicDecoder(const char *name);
	extern DECLSPEC Mix_MusicType SDLCALL Mix_GetMusicType(const Mix_Music *music);
	extern DECLSPEC void SDLCALL Mix_SetPostMix(void (SDLCALL *mix_func)(void *udata, Uint8 *stream, int len), void *arg);
	extern DECLSPEC void SDLCALL Mix_HookMusic(void (SDLCALL *mix_func)(void *udata, Uint8 *stream, int len), void *arg);
	extern DECLSPEC void SDLCALL Mix_HookMusicFinished(void (SDLCALL *music_finished)(void));
	extern DECLSPEC void * SDLCALL Mix_GetMusicHookData(void);
	extern DECLSPEC void SDLCALL Mix_ChannelFinished(void (SDLCALL *channel_finished)(int channel));
	extern DECLSPEC int SDLCALL Mix_RegisterEffect(int chan, Mix_EffectFunc_t f, Mix_EffectDone_t d, void *arg);
	extern DECLSPEC int SDLCALL Mix_UnregisterEffect(int channel, Mix_EffectFunc_t f);
	extern DECLSPEC int SDLCALL Mix_UnregisterAllEffects(int channel);
	extern DECLSPEC int SDLCALL Mix_SetPanning(int channel, Uint8 left, Uint8 right);
	extern DECLSPEC int SDLCALL Mix_SetPosition(int channel, Sint16 angle, Uint8 distance);
	extern DECLSPEC int SDLCALL Mix_SetDistance(int channel, Uint8 distance);
	extern no_parse_DECLSPEC int SDLCALL Mix_SetReverb(int channel, Uint8 echo);
	extern DECLSPEC int SDLCALL Mix_SetReverseStereo(int channel, int flip);
	extern DECLSPEC int SDLCALL Mix_ReserveChannels(int num);
	extern DECLSPEC int SDLCALL Mix_GroupChannel(int which, int tag);
	extern DECLSPEC int SDLCALL Mix_GroupChannels(int from, int to, int tag);
	extern DECLSPEC int SDLCALL Mix_GroupAvailable(int tag);
	extern DECLSPEC int SDLCALL Mix_GroupCount(int tag);
	extern DECLSPEC int SDLCALL Mix_GroupOldest(int tag);
	extern DECLSPEC int SDLCALL Mix_GroupNewer(int tag);
	extern DECLSPEC int SDLCALL Mix_PlayChannelTimed(int channel, Mix_Chunk *chunk, int loops, int ticks);
	extern DECLSPEC int SDLCALL Mix_PlayMusic(Mix_Music *music, int loops);
	extern DECLSPEC int SDLCALL Mix_FadeInMusic(Mix_Music *music, int loops, int ms);
	extern DECLSPEC int SDLCALL Mix_FadeInMusicPos(Mix_Music *music, int loops, int ms, double position);
	extern DECLSPEC int SDLCALL Mix_FadeInChannelTimed(int channel, Mix_Chunk *chunk, int loops, int ms, int ticks);
	extern DECLSPEC int SDLCALL Mix_Volume(int channel, int volume);
	extern DECLSPEC int SDLCALL Mix_VolumeChunk(Mix_Chunk *chunk, int volume);
	extern DECLSPEC int SDLCALL Mix_VolumeMusic(int volume);
	extern DECLSPEC int SDLCALL Mix_HaltChannel(int channel);
	extern DECLSPEC int SDLCALL Mix_HaltGroup(int tag);
	extern DECLSPEC int SDLCALL Mix_HaltMusic(void);
	extern DECLSPEC int SDLCALL Mix_ExpireChannel(int channel, int ticks);
	extern DECLSPEC int SDLCALL Mix_FadeOutChannel(int which, int ms);
	extern DECLSPEC int SDLCALL Mix_FadeOutGroup(int tag, int ms);
	extern DECLSPEC int SDLCALL Mix_FadeOutMusic(int ms);
	extern DECLSPEC Mix_Fading SDLCALL Mix_FadingMusic(void);
	extern DECLSPEC Mix_Fading SDLCALL Mix_FadingChannel(int which);
	extern DECLSPEC void SDLCALL Mix_Pause(int channel);
	extern DECLSPEC void SDLCALL Mix_Resume(int channel);
	extern DECLSPEC int SDLCALL Mix_Paused(int channel);
	extern DECLSPEC void SDLCALL Mix_PauseMusic(void);
	extern DECLSPEC void SDLCALL Mix_ResumeMusic(void);
	extern DECLSPEC void SDLCALL Mix_RewindMusic(void);
	extern DECLSPEC int SDLCALL Mix_PausedMusic(void);
	extern DECLSPEC int SDLCALL Mix_SetMusicPosition(double position);
	extern DECLSPEC int SDLCALL Mix_Playing(int channel);
	extern DECLSPEC int SDLCALL Mix_PlayingMusic(void);
	extern DECLSPEC int SDLCALL Mix_SetMusicCMD(const char *command);
	extern DECLSPEC int SDLCALL Mix_SetSynchroValue(int value);
	extern DECLSPEC int SDLCALL Mix_GetSynchroValue(void);
	extern DECLSPEC int SDLCALL Mix_SetSoundFonts(const char *paths);
	extern DECLSPEC const char* SDLCALL Mix_GetSoundFonts(void);
	extern DECLSPEC int SDLCALL Mix_EachSoundFont(int (SDLCALL *function)(const char*, void*), void *data);
	extern DECLSPEC Mix_Chunk * SDLCALL Mix_GetChunk(int channel);
	extern DECLSPEC void SDLCALL Mix_CloseAudio(void);
### SDL_net.h
	extern DECLSPEC const SDLNet_version * SDLCALL SDLNet_Linked_Version(void);
	extern DECLSPEC int  SDLCALL SDLNet_Init(void);
	extern DECLSPEC void SDLCALL SDLNet_Quit(void);
	extern DECLSPEC int SDLCALL SDLNet_ResolveHost(IPaddress *address, const char *host, Uint16 port);
	extern DECLSPEC const char * SDLCALL SDLNet_ResolveIP(const IPaddress *ip);
	extern DECLSPEC int SDLCALL SDLNet_GetLocalAddresses(IPaddress *addresses, int maxcount);
	extern DECLSPEC TCPsocket SDLCALL SDLNet_TCP_Open(IPaddress *ip);
	extern DECLSPEC TCPsocket SDLCALL SDLNet_TCP_Accept(TCPsocket server);
	extern DECLSPEC IPaddress * SDLCALL SDLNet_TCP_GetPeerAddress(TCPsocket sock);
	extern DECLSPEC int SDLCALL SDLNet_TCP_Send(TCPsocket sock, const void *data,
	        int len);
	extern DECLSPEC int SDLCALL SDLNet_TCP_Recv(TCPsocket sock, void *data, int maxlen);
	extern DECLSPEC void SDLCALL SDLNet_TCP_Close(TCPsocket sock);
	extern DECLSPEC UDPpacket * SDLCALL SDLNet_AllocPacket(int size);
	extern DECLSPEC int SDLCALL SDLNet_ResizePacket(UDPpacket *packet, int newsize);
	extern DECLSPEC void SDLCALL SDLNet_FreePacket(UDPpacket *packet);
	extern DECLSPEC UDPpacket ** SDLCALL SDLNet_AllocPacketV(int howmany, int size);
	extern DECLSPEC void SDLCALL SDLNet_FreePacketV(UDPpacket **packetV);
	extern DECLSPEC UDPsocket SDLCALL SDLNet_UDP_Open(Uint16 port);
	extern DECLSPEC void SDLCALL SDLNet_UDP_SetPacketLoss(UDPsocket sock, int percent);
	extern DECLSPEC int SDLCALL SDLNet_UDP_Bind(UDPsocket sock, int channel, const IPaddress *address);
	extern DECLSPEC void SDLCALL SDLNet_UDP_Unbind(UDPsocket sock, int channel);
	extern DECLSPEC IPaddress * SDLCALL SDLNet_UDP_GetPeerAddress(UDPsocket sock, int channel);
	extern DECLSPEC int SDLCALL SDLNet_UDP_SendV(UDPsocket sock, UDPpacket **packets, int npackets);
	extern DECLSPEC int SDLCALL SDLNet_UDP_Send(UDPsocket sock, int channel, UDPpacket *packet);
	extern DECLSPEC int SDLCALL SDLNet_UDP_RecvV(UDPsocket sock, UDPpacket **packets);
	extern DECLSPEC int SDLCALL SDLNet_UDP_Recv(UDPsocket sock, UDPpacket *packet);
	extern DECLSPEC void SDLCALL SDLNet_UDP_Close(UDPsocket sock);
	extern DECLSPEC SDLNet_SocketSet SDLCALL SDLNet_AllocSocketSet(int maxsockets);
	extern DECLSPEC int SDLCALL SDLNet_AddSocket(SDLNet_SocketSet set, SDLNet_GenericSocket sock);
	extern DECLSPEC int SDLCALL SDLNet_DelSocket(SDLNet_SocketSet set, SDLNet_GenericSocket sock);
	extern DECLSPEC int SDLCALL SDLNet_CheckSockets(SDLNet_SocketSet set, Uint32 timeout);
	extern DECLSPEC void SDLCALL SDLNet_FreeSocketSet(SDLNet_SocketSet set);
	extern DECLSPEC void SDLCALL SDLNet_SetError(const char *fmt, ...);
	extern DECLSPEC const char * SDLCALL SDLNet_GetError(void);
### SDL_shape.h
	extern DECLSPEC SDL_Window * SDLCALL SDL_CreateShapedWindow(const char *title,unsigned int x,unsigned int y,unsigned int w,unsigned int h,Uint32 flags);
	extern DECLSPEC SDL_bool SDLCALL SDL_IsShapedWindow(const SDL_Window *window);
	extern DECLSPEC int SDLCALL SDL_SetWindowShape(SDL_Window *window,SDL_Surface *shape,SDL_WindowShapeMode *shape_mode);
	extern DECLSPEC int SDLCALL SDL_GetShapedWindowMode(SDL_Window *window,SDL_WindowShapeMode *shape_mode);
### SDL_touch.h
	extern DECLSPEC int SDLCALL SDL_GetNumTouchDevices(void);
	extern DECLSPEC SDL_TouchID SDLCALL SDL_GetTouchDevice(int index);
	extern DECLSPEC int SDLCALL SDL_GetNumTouchFingers(SDL_TouchID touchID);
	extern DECLSPEC SDL_Finger * SDLCALL SDL_GetTouchFinger(SDL_TouchID touchID, int index);
### SDL_ttf.h
	extern DECLSPEC const SDL_version * SDLCALL TTF_Linked_Version(void);
	extern DECLSPEC void SDLCALL TTF_ByteSwappedUNICODE(int swapped);
	extern DECLSPEC int SDLCALL TTF_Init(void);
	extern DECLSPEC TTF_Font * SDLCALL TTF_OpenFont(const char *file, int ptsize);
	extern DECLSPEC TTF_Font * SDLCALL TTF_OpenFontIndex(const char *file, int ptsize, long index);
	extern DECLSPEC TTF_Font * SDLCALL TTF_OpenFontRW(SDL_RWops *src, int freesrc, int ptsize);
	extern DECLSPEC TTF_Font * SDLCALL TTF_OpenFontIndexRW(SDL_RWops *src, int freesrc, int ptsize, long index);
	extern DECLSPEC int SDLCALL TTF_GetFontStyle(const TTF_Font *font);
	extern DECLSPEC void SDLCALL TTF_SetFontStyle(TTF_Font *font, int style);
	extern DECLSPEC int SDLCALL TTF_GetFontOutline(const TTF_Font *font);
	extern DECLSPEC void SDLCALL TTF_SetFontOutline(TTF_Font *font, int outline);
	extern DECLSPEC int SDLCALL TTF_GetFontHinting(const TTF_Font *font);
	extern DECLSPEC void SDLCALL TTF_SetFontHinting(TTF_Font *font, int hinting);
	extern DECLSPEC int SDLCALL TTF_FontHeight(const TTF_Font *font);
	extern DECLSPEC int SDLCALL TTF_FontAscent(const TTF_Font *font);
	extern DECLSPEC int SDLCALL TTF_FontDescent(const TTF_Font *font);
	extern DECLSPEC int SDLCALL TTF_FontLineSkip(const TTF_Font *font);
	extern DECLSPEC int SDLCALL TTF_GetFontKerning(const TTF_Font *font);
	extern DECLSPEC void SDLCALL TTF_SetFontKerning(TTF_Font *font, int allowed);
	extern DECLSPEC long SDLCALL TTF_FontFaces(const TTF_Font *font);
	extern DECLSPEC int SDLCALL TTF_FontFaceIsFixedWidth(const TTF_Font *font);
	extern DECLSPEC char * SDLCALL TTF_FontFaceFamilyName(const TTF_Font *font);
	extern DECLSPEC char * SDLCALL TTF_FontFaceStyleName(const TTF_Font *font);
	extern DECLSPEC int SDLCALL TTF_GlyphIsProvided(const TTF_Font *font, Uint16 ch);
	extern DECLSPEC int SDLCALL TTF_GlyphMetrics(TTF_Font *font, Uint16 ch,
	                     int *minx, int *maxx,
	                                     int *miny, int *maxy, int *advance);
	extern DECLSPEC int SDLCALL TTF_SizeText(TTF_Font *font, const char *text, int *w, int *h);
	extern DECLSPEC int SDLCALL TTF_SizeUTF8(TTF_Font *font, const char *text, int *w, int *h);
	extern DECLSPEC int SDLCALL TTF_SizeUNICODE(TTF_Font *font, const Uint16 *text, int *w, int *h);
	extern DECLSPEC SDL_Surface * SDLCALL TTF_RenderText_Solid(TTF_Font *font,
	                const char *text, SDL_Color fg);
	extern DECLSPEC SDL_Surface * SDLCALL TTF_RenderUTF8_Solid(TTF_Font *font,
	                const char *text, SDL_Color fg);
	extern DECLSPEC SDL_Surface * SDLCALL TTF_RenderUNICODE_Solid(TTF_Font *font,
	                const Uint16 *text, SDL_Color fg);
	extern DECLSPEC SDL_Surface * SDLCALL TTF_RenderGlyph_Solid(TTF_Font *font,
	                    Uint16 ch, SDL_Color fg);
	extern DECLSPEC SDL_Surface * SDLCALL TTF_RenderText_Shaded(TTF_Font *font,
	                const char *text, SDL_Color fg, SDL_Color bg);
	extern DECLSPEC SDL_Surface * SDLCALL TTF_RenderUTF8_Shaded(TTF_Font *font,
	                const char *text, SDL_Color fg, SDL_Color bg);
	extern DECLSPEC SDL_Surface * SDLCALL TTF_RenderUNICODE_Shaded(TTF_Font *font,
	                const Uint16 *text, SDL_Color fg, SDL_Color bg);
	extern DECLSPEC SDL_Surface * SDLCALL TTF_RenderGlyph_Shaded(TTF_Font *font,
	                Uint16 ch, SDL_Color fg, SDL_Color bg);
	extern DECLSPEC SDL_Surface * SDLCALL TTF_RenderText_Blended(TTF_Font *font,
	                const char *text, SDL_Color fg);
	extern DECLSPEC SDL_Surface * SDLCALL TTF_RenderUTF8_Blended(TTF_Font *font,
	                const char *text, SDL_Color fg);
	extern DECLSPEC SDL_Surface * SDLCALL TTF_RenderUNICODE_Blended(TTF_Font *font,
	                const Uint16 *text, SDL_Color fg);
	extern DECLSPEC SDL_Surface * SDLCALL TTF_RenderText_Blended_Wrapped(TTF_Font *font,
	                const char *text, SDL_Color fg, Uint32 wrapLength);
	extern DECLSPEC SDL_Surface * SDLCALL TTF_RenderUTF8_Blended_Wrapped(TTF_Font *font,
	                const char *text, SDL_Color fg, Uint32 wrapLength);
	extern DECLSPEC SDL_Surface * SDLCALL TTF_RenderUNICODE_Blended_Wrapped(TTF_Font *font,
	                const Uint16 *text, SDL_Color fg, Uint32 wrapLength);
	extern DECLSPEC SDL_Surface * SDLCALL TTF_RenderGlyph_Blended(TTF_Font *font,
	                        Uint16 ch, SDL_Color fg);
	extern DECLSPEC void SDLCALL TTF_CloseFont(TTF_Font *font);
	extern DECLSPEC void SDLCALL TTF_Quit(void);
	extern DECLSPEC int SDLCALL TTF_WasInit(void);
	extern DECLSPEC int TTF_GetFontKerningSize(TTF_Font *font, int prev_index, int index) SDL_DEPRECATED;
	extern DECLSPEC int TTF_GetFontKerningSizeGlyphs(TTF_Font *font, Uint16 previous_ch, Uint16 ch);
### SDL_vulkan.h
	extern DECLSPEC int SDLCALL SDL_Vulkan_LoadLibrary(const char *path);
	extern DECLSPEC void *SDLCALL SDL_Vulkan_GetVkGetInstanceProcAddr(void);
	extern DECLSPEC void SDLCALL SDL_Vulkan_UnloadLibrary(void);
	extern DECLSPEC SDL_bool SDLCALL SDL_Vulkan_GetInstanceExtensions(
															SDL_Window *window,
															unsigned int *pCount,
															const char **pNames);
	extern DECLSPEC SDL_bool SDLCALL SDL_Vulkan_CreateSurface(
													SDL_Window *window,
													VkInstance instance,
													VkSurfaceKHR* surface);
	extern DECLSPEC void SDLCALL SDL_Vulkan_GetDrawableSize(SDL_Window * window,
	                                                        int *w, int *h);
