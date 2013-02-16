#    This file is part of IBus-BoGo project.
#    Copyright (C) Long T. Dam <longdt90@gmail.com>
#
#    IBus-BoGo is free software: you can redistribute it and/or modify
#    it under the terms of the GNU General Public License as published by
#    the Free Software Foundation, either version 3 of the License, or
#    (at your option) any later version.
#
#    IBus-BoGo is distributed in the hope that it will be useful,
#    but WITHOUT ANY WARRANTY; without even the implied warranty of
#    MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
#    GNU General Public License for more details.
#
#    You should have received a copy of the GNU General Public License
#    along with IBus-BoGo.  If not, see <http://www.gnu.org/licenses/>.
#

install (PROGRAMS
  ibus-bogo-settings
  DESTINATION
  lib/ibus-bogo
  )

install (FILES
  controller.py
  controller.ui
  DESTINATION
  ${BOGO_INSTALL_DIR}/config-gui
  )

install (FILES
  ibus-bogo-settings.desktop
  DESTINATION
  share/applications
)

add_custom_target (translations ALL
  COMMAND pyside-lupdate controller.pro
  COMMAND lrelease controller.pro
  WORKING_DIRECTORY ${CMAKE_SOURCE_DIR}/config-gui
)

FILE (GLOB
 locales "locales/*.qm"
 flags "locales/*.png"
)

install (FILES
  ${locales}
  DESTINATION
  ${BOGO_INSTALL_DIR}/config-gui/locales
  )