import sys
import sdl2
import sdl2.ext
import sdl2.sdlgfx


class Window:
    def __init__(self, size, name):
        self.size = size
        self.name = name
        self.window = sdl2.ext.Window(self.name, size=self.size)

    def fill_Window(self, color):
        r, g, b = color
        COLOR = sdl2.ext.Color(r, g, b)
        sdl2.ext.fill(self.window.get_surface(), COLOR)

    def d1_point(self, x, y, surface, color):
        r, g, b = color
        WHITE = sdl2.ext.Color(r, g, b)
        pixelview = sdl2.ext.PixelView(surface)
        pixelview[y][x] = WHITE

    def d_point(self, x, y, color):
        r, g, b = color
        renderer = sdl2.ext.Renderer(self.window)
        renderer.draw_point([x, y], sdl2.ext.Color(r, g, b))
        renderer.present()
        processor = sdl2.ext.TestEventProcessor()
        processor.run(self.window)

    def draw_raketa(self, turn, l):
        for i in range(100):
            Window.d1_point(self, 500 + turn + i, 710, self.window.get_surface(), (l, l, l))
        for i in range(150):
            Window.d1_point(self, 560 + turn, 710 - i, self.window.get_surface(), (l, l, l))
        for i in range(150):
            Window.d1_point(self, 500 + turn, 710 - i, self.window.get_surface(), (l, l, l))
        for i in range(60):
            Window.d1_point(self, 500 + turn + i, 561, self.window.get_surface(), (l, l, l))
        for i in range(40):
            Window.d1_point(self, 600 + turn - i, 710 - i, self.window.get_surface(), (l, l, l))
        for i in range(30):
            Window.d1_point(self, 500 + turn + i, 561 - i, self.window.get_surface(), (l, l, l))
        for i in range(30):
            Window.d1_point(self, 560 + turn - i, 561 - i, self.window.get_surface(), (l, l, l))
        for i in range(50):
            Window.d1_point(self, 560 + turn + i, 635, self.window.get_surface(), (l, l, l))
        for i in range(50):
            Window.d1_point(self, 500 + turn - i, 635, self.window.get_surface(), (l, l, l))
        for i in range(50):
            Window.d1_point(self, 450 + turn + i, 635 - i, self.window.get_surface(), (l, l, l))
        for i in range(50):
            Window.d1_point(self, 610 + turn - i, 635 - i, self.window.get_surface(), (l, l, l))
        for i in range(40):
            Window.d1_point(self, 500 + turn - i, 710, self.window.get_surface(), (l, l, l))
        for i in range(40):
            Window.d1_point(self, 461 + turn + i, 710 - i, self.window.get_surface(), (l, l, l))

    def run(self):
        sdl2.ext.init()
        self.window.show()
        running = True
        Window.fill_Window(self, (192, 192, 192))
        k = 0
        z = 0
        s = 192
        while running:
            events = sdl2.ext.get_events()
            for event in events:
                if event.type == sdl2.SDL_QUIT:
                    running = False
                    break
                elif event.type == sdl2.SDL_KEYDOWN:
                    if event.key.keysym.sym == sdl2.SDLK_UP:
                        Window.draw_raketa(self, 0, z)
                    if event.key.keysym.sym == sdl2.SDLK_LEFT:
                        Window.draw_raketa(self, k, s)
                        k -= 5
                        Window.draw_raketa(self, k, z)
                    if event.key.keysym.sym == sdl2.SDLK_RIGHT:
                        Window.draw_raketa(self, k, s)
                        k += 5
                        Window.draw_raketa(self, k, z)


                elif event.type == sdl2.SDL_CONTROLLER_BUTTON_X:
                    Window.d_point(self, 10, 20, self.window.get_surface(), (0, 0, 0))
                    Window.d_point(self, 11, 20, self.window.get_surface(), (0, 0, 0))
                    Window.d_point(self, 12, 20, self.window.get_surface(), (0, 0, 0))
                    Window.d_point(self, 13, 20, self.window.get_surface(), (0, 0, 0))
                    Window.d_point(self, 14, 20, self.window.get_surface(), (0, 0, 0))
                self.window.refresh()

        return 0

